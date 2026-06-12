---
title: "Get data from USB and post to MySQL"
date: 2013-06-17
forum: Desktop Environments
---

### Post by vkadal on 2013-06-17
I want to monitor through internet how much power the solar inverter is  generating. The inverter has a USB port. I need your guidance, how to read data from the USB port and post to a MySQL server database using php. I can have another php page to get a report from the MySQL database.

---

### Post by SeijiSensei on 2013-06-17
I don't know about reading the data, but you can post to an SQL database using the DB's command-line client.  For instance, with PostgreSQL I can run a command like:

```
psql -U username -c "insert into table_name (field1, field2) values('0730',100)" dbname
```

---

