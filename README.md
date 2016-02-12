#### apbegneo4j

- cp2
def: index  
A database index is a copy of information in the database for the sole purpose of making retrieving data more efficient.  

- cp4
must have both labels
```
MATCH (n:Product:Promoted) RETURN n;
```

- cp6
csv related
```
LOAD CSV FROM "http://localhost/file.csv" AS row WITH row RETURN row LIMIT 1;
```
if delimiter is not comma
```
LOAD CSV FROM "http://localhost/file.csv" AS line WITH line FIELDTERMINATOR ’;’ RETURN line LIMIT 5;
```

create table by using csv
```
USING PERIODIC COMMIT 500     (commit 500 in batch)
LOAD CSV WITH HEADERS FROM ‘http://localhost/people.csv’ AS row
CREATE (:Person {
        id: row.id,
        first_name: row.`First Name`,
        middle_name: row.`Middle name(s)`
})
```
assign prop by using SET
```
CREATE (p:Person {id: row.id})
SET p.first_name: row.`First Name`
        p.middle_name: row.`Middle name(s)`
})
```

set profile: (neo4j.properties)
```
neostore.nodestore.db.mapped_memory=50M
neostore.relationshipstore.db.mapped_memory=500M
neostore.propertystore.db.mapped_memory=100M
neostore.propertystore.db.strings.mapped_memory=100M
neostore.propertystore.db.arrays.mapped_memory=0M
```




Backing up the Database
```
service neo4j-service stop
```
zip db file:
```
tar -cvf graph.db.tar graph.db
gzip graph.db.tar
```


