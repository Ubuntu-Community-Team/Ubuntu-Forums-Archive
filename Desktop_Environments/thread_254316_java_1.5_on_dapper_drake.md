---
title: "java 1.5 on dapper drake"
date: 2006-09-09
forum: Desktop Environments
---

### Post by cccc on 2006-09-09
hi

I've installed```
apt-get install sun-java5-jdk
```
but get```

# java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

``` 
cannot understand, I have the fresh installation of dapper drake.
```

# dpkg -l | grep java
ii  java-common                            0.24ubuntu2    Base of all Java packages
ii  java-gcj-compat                        1.0.56-0ubuntu1    Java runtime environment using GIJ
ii  libgnucrypto-java                      2.0.1-4ubuntu1    full-featured cryptographic library in Java
ii  libhsqldb-java                         1.8.0.2-1ubuntu1    Java SQL database engine
ii  libjaxp1.2-java                        1.2.01-1ubuntu2    Java XML parser and transformer APIs (DOM, S
ii  libjessie-java                         1.0.1-1ubuntu1    free implementation of the Java Secure Socke
ii  libjline-java                          0.9.1-2ubuntu1    Java library for handling console input
ii  libservlet2.3-java                     4.0-7ubuntu2    Servlet 2.3 and JSP 1.2 Java classes and doc
ii  libxalan2-java                         2.6.0-5ubuntu2    XSL Transformations (XSLT) processor in Java
ii  libxerces2-java                        2.6.2-3ubuntu3    Validating XML parser for Java with DOM leve
ii  libxt-java                             0.20050823-1ubuntu3    An implementation in Java of XSL Transformat
ii  openoffice.org-java-common             2.0.2-2ubuntu12.1    OpenOffice.org office suite Java support arc
ii  sun-java5-bin                          1.5.0-06-1    Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-demo                         1.5.0-06-1    Sun Java(TM) Development Kit (JDK) 5.0 demos
ii  sun-java5-jdk                          1.5.0-06-1    Sun Java(TM) Development Kit (JDK) 5.0
ii  sun-java5-jre                          1.5.0-06-1    Sun Java(TM) Runtime Environment (JRE) 5.0

```

---

### Post by lamego on 2006-09-09
You did install java sun but you didn't made it the default java interpreter.
Read the section "Selecting the default Java version" at:
[https://help.ubuntu.com/community/Java/](https://help.ubuntu.com/community/Java/)

---

### Post by cccc on 2006-09-09
thanks,
```

# update-java-alternatives -l
# update-java-alternatives -s java-1.5.0-sun
 
# apt-get install sun-java5-plugin

```
solved this problem:```

# java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
```

---

