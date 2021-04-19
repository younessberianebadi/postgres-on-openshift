# Postgresql+PHP Demo on openshift

You first use the web console to create the Postgresql Pod:

![GitHub Logo](/images/pg0.png)

![GitHub Logo](/images/pg1.png)

Then, create a PHP Pod using the github repo:

![GitHub Logo](/images/php0.png)

```
https://github.com/younessberianebadi/test-php.git
```
With the same variable environements as Postgressql pod.

PS: You need to add them manually to the deployment

```yaml
URL : postgres
POSTGRES_USER : postgresadmin
POSTGRES_PASSWORD : ''
```

![GitHub Logo](/images/php1.png)

Login to the Postgres Pod using the Terminal CLI provided by Openshift to create the TABLE "people" in the "digiwise" DATABASE:

By first loging in by **psqpl** application to the database:

```bash
psql -d digiwise
```

Creating the TABLE:

```sql
CREATE TABLE people(
fullname text,
birthplace text);
```

Adding some lines:

```sql
INSERT INTO people (fullname, birthplace) VALUES ('person-0', 'city-0');
INSERT INTO people (fullname, birthplace) VALUES ('person-1', 'city-1');
INSERT INTO people (fullname, birthplace) VALUES ('person-2', 'city-2');
```

Granting access to the user used in creating the Pods:

```sql
GRANT ALL PRIVILEGES ON DATABASE digiwise TO postgresadmin;
GRANT ALL PRIVILEGES ON TABLE people TO postgresadmin;
```

That's all!