---
title: "openoffice3 jdbc"
date: 2009-01-29
forum: General Help
---

### Post by textex on 2009-01-29
hello folks

need help on connecting my recently updated (via the .deb package, before OOO3 was available on the repositories) Base to a postgresql database ...when i set the driver class up as "org.postgresql.Driver" on the initial database wizard i obtain the message "the jdbc driver could not be loaded" ...i obtain this message not only with the libpg-java package available via Synaptic, but also with the one i have downloaded from [http://jdbc.postgresql.org](http://jdbc.postgresql.org) ...i started OOO3 from the terminal as next:


$ export CLASSPATH=$CLASSPATH:/usr/share/java/postgresql-8.3-604.jdbc4.jar
$ /opt/openoffice.org3/program/soffice
Exception in thread "Thread-0" java.lang.NoClassDefFoundError: org/postgresql/Driver
Caused by: java.lang.ClassNotFoundException: org.postgresql.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)


my system is a hardy heron, and i obtained the same with all the jars in the /usr/share/java directory: postgresql.jar, postgresql-jdbc3.jar, postgresql-8.3-604.jdbc4.jar and postgresql-jdbc3-8.2.jar

...what should i do?? ...thanxs in advanced

---

