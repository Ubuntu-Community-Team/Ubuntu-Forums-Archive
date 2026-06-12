---
title: "Hibernate for JAVA!"
date: 2006-01-06
forum: General Help
---

### Post by rensu on 2006-01-06
Hello have anyone seen any HOWTO's for Hibernate service for JAVA? I would like to see some of them. Thanks :)

---

### Post by Cliff76 on 2006-01-06
have you looked at the Hibernate website? Personally I'd reccomend you look into Spring JDBC before diving head first into Hibernate.

---

### Post by rensu on 2006-01-06
Didn't understand what do you mean with Spring JDBC?:confused:

---

### Post by emperon on 2006-01-06
[QUOTE=rensu]Didn't understand what do you mean with Spring JDBC?:confused:[/QUOTE]

I am assuming Hibernate refers to Object Mapping technology for databases. Spring is also a framework ([www.springframework.org](www.springframework.org)) proposed to make easier life for application developers (mainly J2EE or web applications). JDBC is something you should know from java (Java database connection) And Spring JDBC is the JDBC implamentaiton of spring

---

### Post by jwenting on 2006-01-07
Spring is comething completely different from Hibernate.
It can use Hibernate, but it's certainly no replacement for it.

There are some nice tutorials that come with Hibernate. Those together with O'Reilly's "Hibernate developer's notebook" (which is for Hibernate 2, so you need to study some to make it work with 3.1) together should get you started.
You may want to use another RDBMS from HsqlDB though, as the latest versions have some weird behaviour in embedded mode that can cause all changes to the database to be lost on termination (it seems to keep all changes in memory at runtime and fail to write them out to disk on shutdown unless specific commands are issued first).

Spring JDBC is no different from regular JDBC except it adds some JNDI stuff and connection pooling capability.

---

### Post by rensu on 2006-01-07
Im pretty new in JAVA and just wanted to have some good stuff for developing it. And haven't seen any good howtos to install:
JBoss J2EE server, Hibernate or Spring JDBC. Any advices what would be better?

---

### Post by emperon on 2006-01-17
Emule !

---

