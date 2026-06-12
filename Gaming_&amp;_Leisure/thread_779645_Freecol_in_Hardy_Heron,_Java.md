---
title: "Freecol in Hardy Heron, Java"
date: 2008-05-02
forum: Gaming &amp; Leisure
---

### Post by moon2js on 2008-05-02
```
$ freecol
exec: 26: /usr/lib/jvm/java-6-sun/jre/bin/java: not found
$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
$ 
```

Any one know the best way to fix this?

---

### Post by ad_267 on 2008-05-02
You could install sun-java or create a symbolic link to /usr/bin/java from /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by mringer on 2008-05-31
The following worked for me. 

You need Sun's version of Java, apparently UB comes with GNU java, incompatible.
One source is

 [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

I guessed the version called linux RPM. When you unpack, it does not have an 
install script, so you have to install by hand.

Suppose it has unpacked into directory  xyz  do

sudo cd /usr/lib/jvm/java-6-sun
sudo ln -s  xyz  jre

Notes: 1: It was extremely important that the 'file not found' message gave the
full pathname. 
2. The freecol package should depend on a suitable Java package.

---

### Post by ad_267 on 2008-05-31
Sun's version of Java is available in the Ubuntu repositories, it's called sun-java6-bin. You may need to enable extra repositories in synaptic  by going to Settings - Repositories and ticking the restricted and multiverse repositories.

It's a lot better idea to install from the repositories than having to download and install from a script or copy files yourself.

---

### Post by moon2js on 2008-07-08
```
sudo ln -s /usr/lib/jvm/java-6-openjdk/ /usr/lib/jvm/java-6-sun
```

That's what I did to point freecol to the newer Java in Hardy, and it works fine. If anyone sees anything wrong with this or knows of some headaches it causes, let me know. This probably affects any Java app looking for java-6-sun.

---

