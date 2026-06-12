---
title: "free LabView equivalent?"
date: 2012-07-27
forum: Education &amp; Science
---

### Post by memilanuk on 2012-07-27
Anyone?  I'm interested in setting up some measuring/recording/control for a home/hobby project, and so far it looks like my choices are either a) LabView ($$$$) or roll-my-own-interface (lots and lots of time spent plus trial-n-error).  Kind of hoping for something in between...

---

### Post by praseodym on 2012-08-01
What about "myOpenlab"?

[http://www.myopenlab.de/](http://www.myopenlab.de/)

Only German/Spanish HP, but an English forum part:

[http://myopenlab.informe.com/myopenlab-english-df1.html](http://myopenlab.informe.com/myopenlab-english-df1.html)

---

### Post by memilanuk on 2012-08-01
Looks good, not sure why they have an english-language forum if everything (including docs) is in German/Spanish?

---

### Post by praseodym on 2012-08-02
Unpack the 30MB download and start via:

> sudo sh ./start_linux
You can choose English there.

But sadly there was an error here, maybe because of Java 7?!

---

### Post by praseodym on 2012-08-02
Hi,

it does not work with Java 7 from Oracle (Java 6 from Sun/Oracle not tested), but with OpenJDK6:

```
sudo apt-get install openjdk-6-jdk openjdk-6-source openjdk-6-demo openjdk-6-doc openjdk-6-jre-headless openjdk-6-jre-lib openjdk-jre icedtea6-plugin
```
Then change to openjdk6:

```
sudo update-alternatives --config java 
```
Start with
```
java -jar c-exp-lab.jar Elements
```
or
```
sh ./start_linux
```

---

