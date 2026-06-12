---
title: "eclipse won't run after install"
date: 2008-03-01
forum: Desktop Environments
---

### Post by RyanZec on 2008-03-01
after installing eclipse i get an error saying:

JVM terminated. Exit code=1
/usr/lib/j2se/1.4/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata ad0062
-install /usr/lib/eclipse
-vm /usr/lib/j2se/1.4/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

anyone know what is wrong?

---

### Post by RyanZec on 2008-03-01
i figured it out, i needed to install version 1.5 of java

---

