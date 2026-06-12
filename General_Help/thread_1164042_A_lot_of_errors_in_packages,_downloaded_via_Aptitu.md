---
title: "A lot of errors in packages, downloaded via Aptitude ( urgent help needed ) .."
date: 2009-05-19
forum: General Help
---

### Post by ActiveFrost on 2009-05-19
What to do now and why it happened ?

[[IMG]http://i40.tinypic.com/2cncz8k.png[/IMG]]("http://i44.tinypic.com/b3lg8y.png")
Click on the image for a higher resolution.

---

### Post by qjmoss on 2009-05-19
You have a java issue, as you can see. try to reinstall java

---

### Post by ActiveFrost on 2009-05-19
Ok, looks like Java is working now ( reinstalled ), though, what means unixodbc and odbcinst1debian1 ? Should I reinstall them ( if they are "packages" ) ?

Damn, again - tried to install JDK and got this as an output ( 100x ) :
```
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:2357: parser error : Opening and ending tag mismatch: tocseccsect3 line 2356 and tocsect3
</tocsect3>
```

How to get rid of these errors ?

---

### Post by Soul-Sing on 2009-05-19
JDK, you mean openjdk? running two java appl. isn't the right thing to do. (sun java and openjdk)

---

### Post by qjmoss on 2009-05-19
> **leoquant said:**
> JDK, you mean openjdk? running two java appl. isn't the right thing to do. (sun java and openjdk)

Wait your trying to run two java app. at the same time?

---

### Post by ActiveFrost on 2009-05-19
> **qjmoss said:**
> Wait your trying to run two java app. at the same time?

No ! I'm trying to install sun-java6-bin, sun-java6-jre, sun-java6-plugin, sun-java6-jdk.
Removed .deb packages from cache ( /var/cache/apt/archives/ ) and reinstalled ( including downloading ) - still the same error :o
Any workarounds ?

---

### Post by Soul-Sing on 2009-05-19
sun java jdk is only used for webdevel.
these are nec.: sun-java6-bin, sun-java6-jre, sun-java6-plugin

---

### Post by ActiveFrost on 2009-05-19
> **leoquant said:**
> sun java jdk is only used for webdevel.
these are nec.: sun-java6-bin, sun-java6-jre, sun-java6-plugin

Thanks for the tip, however, jdk is required to run Eclipse ( PHP/Java, etc. ), so .. I simply need it.
Anyway, problem is solved in the way of installing 9.04 ( Jaunty ) :D

---

