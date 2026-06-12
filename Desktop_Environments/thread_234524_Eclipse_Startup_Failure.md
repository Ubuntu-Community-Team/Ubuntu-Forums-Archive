---
title: "Eclipse Startup Failure"
date: 2006-08-11
forum: Desktop Environments
---

### Post by asv on 2006-08-11
Hello, I'm trying to run eclipse available through apt. When launching eclipse I get the following error:
```

JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06//bin/java
-jar startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /home/asv/bin/eclipse
-name Eclipse
-showsplash 600
-exitdata 1bc001b
-vm /usr/lib/jvm/java-1.5.0-sun-1.5.0.06//bin/java
-vmargs
-jar startup.jar 
```

```
asv@asv:~$ eclipse
Unable to access jarfile startup.jar

asv@asv:~$ sudo update-java-alternatives -l
Password:
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
asv@asv:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)
asv@asv:~$
```

Any ideas?

---

