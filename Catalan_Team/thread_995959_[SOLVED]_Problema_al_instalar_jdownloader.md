---
title: "[SOLVED] Problema al instalar jdownloader"
date: 2008-11-28
forum: Catalan Team
---

### Post by Dr.Rwh on 2008-11-28
Hola a tots, soc un usuari novell, que mica en mica va aprenent :p

El cas és que necessito el gestor de descàrregues Jdownloader. Tinc el java instalat, però al intentar executar el jdownloader desde el terminal ( com a root, ja que en usuari normal em diu que no tinc permisos )em diu el seguent:

```
sergi@SergiC:~/jdownloader_v0.3668$ su
Password: 
root@SergiC:/home/sergi/jdownloader_v0.3668# java -jar JDownloader.jar
28/11/2008 17:22:38 - INFO [jd.config.DatabaseConnector(<init>)] -> Loading database
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.Runtime.load0(Runtime.java:787)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.System.load(System.java:1022)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.System.loadLibrary(System.java:1047)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.awt.Dimension.<clinit>(Dimension.java:87)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.misc.Unsafe.ensureClassInitialized(Native Method)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.UnsafeFieldAccessorFactory.newFieldAccessor(UnsafeFieldAccessorFactory.java:43)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.ReflectionFactory.newFieldAccessor(ReflectionFactory.java:140)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Field.acquireFieldAccessor(Field.java:936)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Field.getFieldAccessor(Field.java:917)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Field.getLong(Field.java:546)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.getDeclaredSUID(ObjectStreamClass.java:1631)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.access$700(ObjectStreamClass.java:69)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass$2.run(ObjectStreamClass.java:442)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.<init>(ObjectStreamClass.java:430)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.lookup(ObjectStreamClass.java:327)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.initNonProxy(ObjectStreamClass.java:564)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readNonProxyDesc(ObjectInputStream.java:1600)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1513)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1749)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.util.HashMap.readObject(HashMap.java:1047)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.GeneratedMethodAccessor1.invoke(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Method.invoke(Method.java:616)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.invokeReadObject(ObjectStreamClass.java:991)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readSerialData(ObjectInputStream.java:1865)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1770)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at org.hsqldb.lib.InOutUtil.deserialize(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at org.hsqldb.types.JavaObject.getObject(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at org.hsqldb.jdbc.jdbcResultSet.getObject(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.config.DatabaseConnector.<init>(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.utils.JDUtilities.getDatabaseConnector(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.config.SubConfiguration.<init>(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.utils.JDUtilities.getSubConfig(Unknown Source)
28/11/2008 17:22:38 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.Main.main(Unknown Source)
root@SergiC:/home/sergi/jdownloader_v0.3668# 

```

Gràcies per el vostre temps! :)

Salut

---

### Post by papapep on 2008-11-28
El més important: **[COLOR="Red"]NO[/COLOR]** s'ha d'executar programes com a root, a no ser que siguin programes d'administració del sistema. Et pot provocar un desgavell total al sistema.
"Pulutant", modifica el propietari i/o permisos del jdownloader de la següent manera:

```
sudo chown sergi:sergi /home/sergi/jdownloader_v0.3668/ -R
```

i

```
sudo chmod 755 /home/sergi/jdownloader_v0.3668/ -R
```

i torna a provar a executar-lo, però ara com a usuari normal.

---

### Post by Dr.Rwh on 2008-11-28
Gràcies per respondre, però el error persisteix.

```
sergi@SergiC:~/jdownloader_v0.3668$  java -jar JDownloader.jar
28/11/2008 18:16:16 - INFO [jd.config.DatabaseConnector(<init>)] -> Loading database
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.Runtime.load0(Runtime.java:787)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.System.load(System.java:1022)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.System.loadLibrary(System.java:1047)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.awt.Dimension.<clinit>(Dimension.java:87)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.misc.Unsafe.ensureClassInitialized(Native Method)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.UnsafeFieldAccessorFactory.newFieldAccessor(UnsafeFieldAccessorFactory.java:43)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.ReflectionFactory.newFieldAccessor(ReflectionFactory.java:140)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Field.acquireFieldAccessor(Field.java:936)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Field.getFieldAccessor(Field.java:917)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Field.getLong(Field.java:546)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.getDeclaredSUID(ObjectStreamClass.java:1631)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.access$700(ObjectStreamClass.java:69)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass$2.run(ObjectStreamClass.java:442)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.<init>(ObjectStreamClass.java:430)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.lookup(ObjectStreamClass.java:327)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.initNonProxy(ObjectStreamClass.java:564)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readNonProxyDesc(ObjectInputStream.java:1600)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1513)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1749)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.util.HashMap.readObject(HashMap.java:1047)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.GeneratedMethodAccessor1.invoke(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.reflect.Method.invoke(Method.java:616)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectStreamClass.invokeReadObject(ObjectStreamClass.java:991)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readSerialData(ObjectInputStream.java:1865)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1770)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at org.hsqldb.lib.InOutUtil.deserialize(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at org.hsqldb.types.JavaObject.getObject(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at org.hsqldb.jdbc.jdbcResultSet.getObject(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.config.DatabaseConnector.<init>(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.utils.JDUtilities.getDatabaseConnector(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.config.SubConfiguration.<init>(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.utils.JDUtilities.getSubConfig(Unknown Source)
28/11/2008 18:16:16 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.Main.main(Unknown Source)
sergi@SergiC:~/jdownloader_v0.3668$ 

```

gràcies!

---

### Post by papapep on 2008-11-28
A veure quines màquines virtuals de java tens instal·lades...

```
update-java-alternatives -l

```

i els paquets relacionats:

```
sudo aptitude search jdk|grep ^i
```

---

### Post by Dr.Rwh on 2008-11-28
Gràcies per respondre tan ràpid ;)

```
sergi@SergiC:~$ update-java-alternatives -l
java-6-cacao 1059 /usr/lib/jvm/java-6-cacao
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
sergi@SergiC:~$ sudo aptitude search jdk|grep ^i
[sudo] password for sergi: 
i A openjdk-6-jre-headless          - OpenJDK Java runtime, using Hotspot JIT (h
i A openjdk-6-jre-lib               - OpenJDK Java runtime (architecture indepen
i   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
sergi@SergiC:~$ 

```

---

### Post by papapep on 2008-11-28
Fes això:

```
sudo update-alternatives java
```

i tria aquesta:

```
sun-java6-jdk  
```

i torna a provar a executar el programa.

---

### Post by Dr.Rwh on 2008-11-28
```
sergi@SergiC:~$ sudo update-alternatives java
update-alternatives: l'argument «java» és desconegut
sergi@SergiC:~$ 

```

---

### Post by papapep on 2008-11-28
Perdó, m'he oblidat del modificador...:

```
sudo update-alternatives --config java
```

---

### Post by Dr.Rwh on 2008-11-28
Em dona a escollir entre aquets tres:

-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-cacao/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by papapep on 2008-11-28
el 3

---

### Post by Dr.Rwh on 2008-11-30
Gràcies, solucionat :)

---

