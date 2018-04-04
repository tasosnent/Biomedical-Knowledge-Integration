# Biomedical Knowledge Semantic Integration
A platform to automatically retrieve and integrate knowledge relevant to a disease based on a semantic graph representation.

## Structure
The platform is structured into two individual parts, available in the repositories referenced below :
### Harvesting of Biomedical Knowledge: [Biomedical Harvesters](https://github.com/tasosnent/BiomedicalHarvesters)
* Online retrieval of available up-to-date biomedical literature from PubMed and PMC
  * *Output:* The natural language text of the articles harvested (i.e. abstract or full-text) and relations of articles with their topic areas (i.e. MeSH headings)
* Preprocessing of structured biomedical resources like OBO ontologies and DrugBank 
  * *Input:* The files of the resources to be harvested
  * *Output:* Relations between biomedical entities from structured resources (e.g. "concept a" is a "concept b", or "drug a" interacts with "drug b" )  
* This step produces data sets in a simple JSON format stored in individual MongoDB collections
### Semantic Enrichment of Biomedical Knowledge: [Medknow](https://github.com/kbogas/medknow)
* Extraction of knowledge from literature natural language text
  * *Input:* The MongoDB collection with natural language text of articles 
  * *Output:* Concepts occurring in article text and relations between occurring concepts
* Semantic indexing of harvested relations in a common framework as a semantic graph 
  * *Input:* The MongoDB collection of relations between entities (including relations of articles with their topic areas and relations from structured resources)
  * *Output:* Relations between entities represented in a common UMLS-based semantic framework.
* This step produces an integrated knowledge graph in a Neo4j database where knowledge from all harvested resources is uniformly available through graph queries.
