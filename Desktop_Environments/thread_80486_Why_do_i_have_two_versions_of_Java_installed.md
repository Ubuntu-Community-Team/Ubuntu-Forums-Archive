---
title: "Why do i have two versions of Java installed?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by sk545 on 2005-10-22
Its weird, if i just do plain '$ java -version' i get:

$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

But if i go to '/usr/lib/j2sdk1.5-sun/bin' and run 'java -version' from that directory, i get:

```

$ /usr/lib/j2sdk1.5-sun/bin$ ./java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)

```

Which one should i be using? Do i need two of them?  I would rather use 1.5, if possible.

Things i have installed dealing with java:

```

$ sudo dpkg --get-selections | grep java
java-gcj-compat                                 install
libcommons-cli-java                             install
libgnucrypto-java                               install
libgnujaxp-java                                 install
libhsqldb-java                                  install
libjaxp1.2-java                                 install
libjessie-java                                  install
liblog4j1.2-java                                install
libseda-java                                    install
libservlet2.3-java                              install
libswt-gtk-3.1-java                             install
libxalan2-java                                  install
libxerces2-java                                 install
libxt-java                                      install
openoffice.org2-java-common                     install

```

```

$ sudo dpkg --get-selections | grep j2 
sun-j2re1.5                                     install
sun-j2sdk1.5                                    install

```

Thx.

---

### Post by jeremy on 2005-10-22
Try
sudo update-alternatives --config java
and select the one you want.

---

### Post by RYX on 2005-10-22
It is kind of mysterious that you have Java SDK 1.5 installed and don't even know it - Ubuntu 5.10 comes bundled with Java 1.4 and it takes quite a bit of action to get Java 1.5 installed ... (a VERY good tutorial for doing that is here: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)) . . .

However, which version you need depends on which Java-based applications you want to use. If you intend to use Azureus or newer versions of Eclipse (3.1+), you definetly want to use Java 1.5. If the programs you want to use are working with 1.4, go on and use that version (because native support is sometimes better than upgrading by hand anytime a new upgrade is released ;) ) ...

Hope I could help...

---

### Post by sk545 on 2005-10-22
> It is kind of mysterious that you have Java SDK 1.5 installed and don't even know it
I think i know what happened...i might have installed 1.5 long time ago through another repo and forgot about it.  Thx for the fix though, guys.

---

### Post by sk545 on 2005-10-22
quick question: Which java binary is better to use? The one that comes with JRE or J2SDK?  I have two right now:

        /usr/lib/j2re1.5-sun/bin/java
        /usr/lib/j2sdk1.5-sun/bin/java

---

