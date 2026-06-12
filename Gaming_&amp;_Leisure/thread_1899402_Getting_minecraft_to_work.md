---
title: "Getting minecraft to work"
date: 2011-12-23
forum: Gaming &amp; Leisure
---

### Post by nemodot on 2011-12-23
I'm trying to play Minecraft classic form the browser. The screen goes black and nothing happens.

I've read you must delete icedtea6-plugin and install sun-java6-plugin but I had it already installed and now i get a missing plugin notice whenever I try to run it form chrome or firefox.

How can I make the sun-java6-plugin to work with my browsers?

Using ubuntu 10.10

---

### Post by Perfect Storm on 2011-12-23
Sun java have been disabled because of serious security bugs in sun/oracle Java and also that Oracle have change license policy for Java. So if you want to use Oracle Java you need to install it manually.

---

### Post by nemodot on 2011-12-23
Thanks for the answer!

But How do I do that? It's already instaled, do I have to purge it and then compile sun java?

---

### Post by Perfect Storm on 2011-12-23
> **nemodot said:**
> Thanks for the answer!

But How do I do that? It's already instaled, do I have to purge it and then compile sun java?

The package you have are empty packages, you can uninstall them. There's a installation instruction on Sun Oracle homepage;
[http://www.java.com/en/download/manual.jsp?locale=en](http://www.java.com/en/download/manual.jsp?locale=en)

---

### Post by ergo-proxy on 2011-12-23
Here is the instruction how to do it: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by nemodot on 2011-12-23
But I'm using Sun Java, it is installed and running everything but minecraft :confused:

---

### Post by Perfect Storm on 2011-12-23
> **nemodot said:**
> But I'm using Sun Java, it is installed and running everything but minecraft :confused:

Are you not sure the other things are running Openjava.

---

### Post by nemodot on 2011-12-24
All openjdk packages are uninstalled. All sun java packages are installed.

---

### Post by ergo-proxy on 2011-12-24
Type: 

> which java

> java -version

---

### Post by nemodot on 2011-12-24
```
esteban@esteban:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Client VM (build 20.1-b02, mixed mode, sharing)
esteban@esteban:~$ 
```

---

### Post by ergo-proxy on 2011-12-26
Did you try to run from a terminal? 

> java -jar minecraft.jar

---

