---
title: "Java question.."
date: 2009-02-26
forum: General Help
---

### Post by Pinejoker on 2009-02-26
I know its silly question.. i just update the ubuntu 8.10 now my question is, how can i know if i have java?

---

### Post by 3rdalbum on 2009-02-26
I imagine there's a test page at [www.sun.com](www.sun.com) somewhere, as they are the biggest sponsors of Java.

---

### Post by Pinejoker on 2009-02-26
cant find the testing area of java...

---

### Post by 3rdalbum on 2009-02-26
[http://www.javatester.org/version.html]("http://www.javatester.org/version.html")

---

### Post by FluffyElmo on 2009-02-26
That will work if you have the web plug-in, if you don't in a  terminal window you can type:
```
java -version
```

---

### Post by Pinejoker on 2009-02-26
> **FluffyElmo said:**
> That will work if you have the web plug-in, if you don't in a  terminal window you can type:
```
java -version
```



thanks

---

### Post by zika on 2009-02-26
I've doing a little of housekeeping of my AMD_64 Interpid machine and I found (again) that I have 3 versions of Java (nicely working in FF and elsewhere, knock on the wood). should I and what of them should I uninstall? and what of these should I choose for default?

```
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-cacao/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
java - status is manual.
 link currently points to /usr/lib/jvm/java-6-openjdk/jre/bin/java

/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-cacao/jre/bin/java - priority 1059
 slave java.1.gz: /usr/lib/jvm/java-6-cacao/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-6-openjdk/jre/bin/java.

Synaptic:
openjdk-6-jre{,-lib,-headless}
cacao-oj6-jre-{lib,headless}
sun-java6-{bin,jre}
```

---

### Post by FluffyElmo on 2009-02-26
I wouldn't worry about it, you are using the most current version. All the other two will do is take up some disk space, they shouldn't affect anything.

---

### Post by stim on 2009-02-26
Since openjdk is listed as the default, you could uninstall the other two.  Having multiple versions of java installed will not hurt your system.  I have several (I think 4) installed on my system. I even have 1.4 because I need to run some legacy apps.

---

### Post by zika on 2009-02-26
> **FluffyElmo said:**
> I wouldn't worry about it, you are using the most current version. All the other two will do is take up some disk space, they shouldn't affect anything.
I have another java laying around, that is this (alpha) jre1.6.0_14 and it is not in the list. it resides in /opt/java that I update every time new version arrives. would the right syntax to install it be:```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/bin/java" 1
sudo update-alternatives --set java /opt/java/bin/java
``` ...?

it seems that I'm using the latest plugin but I'm not using the latest jre that accompanies it.

**update:** it worked, now the plugin is re-paired with its jre ... ;) now I have, also,  4 java's but who cares ... ;)

now I hve:```
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-cacao/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
*         4    /opt/java/bin/java

java - status is manual.
 link currently points to /opt/java/bin/java
/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-cacao/jre/bin/java - priority 1059
 slave java.1.gz: /usr/lib/jvm/java-6-cacao/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
/opt/java/bin/java - priority 1
Current `best' version is /usr/lib/jvm/java-6-openjdk/jre/bin/java.
```what is the meaning of this "priority" ? it seems that I've picked the latest but with the least priority ... :)

---

### Post by Pinejoker on 2009-02-27
Thanks guys.. it helps me alot. =)  I just want to make sure that i have java... ubuntu 8.10 Okie..

---

