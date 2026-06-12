---
title: "Which java package?"
date: 2009-02-16
forum: General Help
---

### Post by vaibhav on 2009-02-16
I'm using Ubuntu 8.04 and I wanted to install the Java JRE. Searching synaptic I found sun, openjdk and icedtea packages for the same. Which one should I select? And what's the difference between these?

---

### Post by x33a on 2009-02-16
install the sun package.

as for the other two:

[http://en.wikipedia.org/wiki/OpenJDK](http://en.wikipedia.org/wiki/OpenJDK)

[http://en.wikipedia.org/wiki/IcedTea](http://en.wikipedia.org/wiki/IcedTea)

---

### Post by Tim Sharitt on 2009-02-16
Sun is the official java package, while icedtea is an open source implementation. I'm not real sure about openjdk, but from the name I would guess that it is probably just the development kit and not what you would want to run java applications.

The open source java runtime environments may run everything fine, but you could possibly find incompatibilities with some applications.

---

### Post by binbash on 2009-02-16
Install sun java if you dont want to encounter with problems, dont forget to install the plugin so you can play java applets at firefox etc

---

### Post by jespdj on 2009-02-16
> **Tim Sharitt said:**
> Sun is the official java package, while icedtea is an open source implementation. I'm not real sure about openjdk, but from the name I would guess that it is probably just the development kit and not what you would want to run java applications.
Sun is making their implementation of Java open source. [OpenJDK](http://openjdk.java.net/) is Sun's project for doing this. Making Sun Java open source is a lot of work; Sun used some third-party components (for example for font rendering) which they can't just open up the code for, since they don't own that code. In the OpenJDK project, they are replacing those third-party components with open source components.

The OpenJDK version of Java that you can install on Ubuntu is about 95% the same as Sun Java 6. Almost all Java software works without any problem, but some things do not (notably Java applets that some banks are using for online banking).

IcedTea is a project started by Red Hat before Sun started its OpenJDK project, but which has a similar goal. Currently, when you want to use Java in Firefox using OpenJDK, you'll have to use the browser plug-in from IcedTea (which uses OpenJDK Java to run applets).

Note that the next version of Sun Java (probably due somewhere in 2010) will be based on OpenJDK Java - so, Sun Java 7 will be the same as OpenJDK Java 7.

The safest and most compatible version of Java to use at the moment is Sun Java 6. On Ubuntu 8.10 you can install it like this:
```
sudo apt-get install sun-java6-plugin
```
This will install Sun Java 6 including Sun's browser plug-in.

Note that for 64-bit systems there's no Sun Java browser plug-in the version of Sun Java that's in the repository. Sun recently released Java 6 update 12 which includes a 64-bit browser plug-in, but this is not in the Ubuntu repo yet (it will be in Jaunty). On a 64-bit system, you can manually install Sun Java 6 update 12 (instructions can be found in posts in the 64-bit forum) or you can use the IcedTea plugin and OpenJDK Java.

---

### Post by vaibhav on 2009-02-18
Thanks guys for the replies! I have installed the Sun packages for Java 6 and all's working well.

---

