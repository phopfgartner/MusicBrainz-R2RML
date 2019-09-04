MusicBrainz Virtual Knowledge Graph
===================================

R2RML mappings for the MusicBrainz schema on an entity-by-entity basis.

While these mappings have been used in the past mainly for materializing the RDF graph, we propose to treat the RDF graph as virtual. For that purpose, we use the Virtual Knowledge Graph (VKG) system [Ontop](https://github.com/ontop/ontop) to set up a SPARQL endpoint.

## Requirements

### MusicBrainz Database

A virtual machine is available (for use with VirtualBox, VMware, etc.) with a replicated MusicBrainz at
https://musicbrainz.org/doc/MusicBrainz_Server/Setup.

Note that the file `musicbrainz_config.properties` must reflect your DB name:
* `musicbrainz_db` is the default for a snapshot
* `musicbrainz_db_slave` is the default for a replicated database

### Apache Jena
Download [Apache Jena](https://jena.apache.org/download/) and define the `JENA_DIR` environment variable.


### Ontop >= 3.0.0
Download `ontop-cli` on https://github.com/ontop/ontop/releases and define the `ONTOP_DIR` environment variable.


## Merging the mapping files

```bash
cd MusicBrainz-R2RML
${JENA_DIR}/bin/rdfcat -out Turtle mappings/*.ttl > merged-mapping.ttl
```

## Downloading and merging the ontology files


## SPARQL endpoint


## Materialization of the RDF graph
```bash
${ONTOP_DIR}/ontop endpoint --mapping merged-mapping.ttl -p musicbrainz_config.properties
```