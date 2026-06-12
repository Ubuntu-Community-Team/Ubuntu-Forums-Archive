---
title: "Java 7 Installation"
date: 2011-09-03
forum: Desktop Environments
---

### Post by anieruddha on 2011-09-03
I install Sun-Jdk 7 by following steps mention in 

[http://strug.wordpress.com/2009/02/22/installing-java-7-snapshot-on-ubuntu/](http://strug.wordpress.com/2009/02/22/installing-java-7-snapshot-on-ubuntu/)

Now the problem is 


```

aniruddha@aniruddha-laptop:~/works/java$ java -version
java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b17, mixed mode)

```

```

aniruddha@aniruddha-laptop:~/works/java$ javac -version
javac 1.6.0_26

```

---

### Post by doobrie on 2011-09-03
I've not installed Java 7 yet, but I imagine you need to run:

```
update-alternatives --config javac
```

---

### Post by anieruddha on 2011-09-03
> **doobrie said:**
> I've not installed Java 7 yet, but I imagine you need to run:

```
update-alternatives --config javac
```

Nope after executing the above command, it says 
```
Nothing to configure.
```

but javac version still 1.6.XX

---

### Post by raja.genupula on 2011-09-03
java 7 is the run time environment in your system . i mean if you installed any java supported software then to run them successfully you need java . so here that java version 7 (JRE).


to compile the java programs you need JDK that JDK is 6 th version .

---

### Post by jfed on 2011-09-03
This might be better off in the "General Help" section. It doesn't have to do much with Desktop Environments :P

---

### Post by anieruddha on 2011-09-04
Hey thanks for reply.

As a workaround I point java-6-sun link to jdk1.7.0 instead of jdk1.6.xx


But I found solution here : 
[http://brunoreis.com/tech/intalling-java-ubuntu-natty/](http://brunoreis.com/tech/intalling-java-ubuntu-natty/)

---

