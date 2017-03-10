# ODA Kapa

Contains the information for integration of the ODA system to the National Service Architecture KaPA.

* [Working with diagrams](diagrams.md)
* [Codes and code systems](codesets.md)
* [Integrations](integrations.md)

## Deployment architecture

![](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/omahoito/oda-kapa/master/deployment.plantuml?1) <!--- This generates a picture based on deployment.md. To change the counter in the url above, i.e. deployment.md?13 -> deployment.md?14 --->

###Peruskokoonpanot
####Peruskokoonpano 
- 3+n kappaletta
- CentOS 7, Ubuntu 16 or Debian 8
- 32G+ RAM
- 4+ CPU
- 250G+ SSD storage
- 2 NIC

####Integraatiopalvelin
- 2+n kappaletta
- CentOS 7, Ubuntu 16 or Debian 8
- 16G+ RAM
- 4+ CPU
- 250G+ SSD storage
- 2 NIC

####Proxypalvelin
- 2+n kappaletta
- CentOS 7, Ubuntu 16 or Debian 8
- 16G+ RAM
- 4+ CPU
- 250G+ SSD storage
- 4 NIC

####Continuous Integration Server
- 1 kappale
- CentOS 7, Ubuntu 16 or Debian 8
- 32G+ RAM
- 8+ CPU
- 250G+ SSD storage
- 4 NIC

###Kapasiteettipalveluja
- Backup

###Asiantuntijapalvelut
- Sysadmin palvelut 24/7
- Ylläpitoasiantuntija t&m
- Konesaliasiantuntija/arkkitehti t&m

###Optiona 
###Kapasiteettipalveluja optiona
- SAN kasvattaminen ainakin 100T asti. SAN redundancy respective to network environment.
- NAS low tier 
- Virtuaalipalvelin

####Database Server 
- 2+n kappaletta
- CentOS 7, Ubuntu 16 or Debian 8
- 32G+ RAM
- 4+ CPU
- SAN 1T+ Storage
- 2 NIC

####Logging Server 
- 2+n
- CentOS 7, Ubuntu 16 or Debian 8
- 16G+ RAM
- 4+ CPU
- SAN 1T+ Storage
- 2 NIC

####Integration Security Server
- CentOS 7 or Ubuntu 14
- 16G+ RAM
- 4+ CPU
- 250G+ SSD storage
- 2 NIC

####Temporary Server 
- CentOS 7, Ubuntu 16 or Debian 8
- 8G+ RAM
- 2+ CPU
- 100G+ storage
- 1 virtual NIC

####Verkkopalveluja
- Palomuuri, VLAN ja Loadbalancer

###Symbol
| Logical connections        | Optional connections           | Physical connections  |
| ------------- |:-------------:| -----:|
| ![](logical.png)      | ![](optional.png) | ![](physical.png) |



## Logical diagram

The e-services for your well-being (ODA) application server provides data in json form and adhering to the FHIR healtcare standard for information provision. Since KaPA currently only serves information through SOAP, the data is passed through an ESB server which converts the data from json to xml. A security server acts as a certification provider for the data. Both ODA and KAPA have their own security servers to ensure the validity of the data. Besides Kapa, ODA also has its own interface to the internet through a proxy, which can serve information both directly as a REST server, and through a web front end server.


![](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/omahoito/oda-kapa/master/logical.plantuml?1) <!--- This generates a picture based on deployment.md. To change the counter in the url above, i.e. deployment.md?13 -> deployment.md?14 --->
