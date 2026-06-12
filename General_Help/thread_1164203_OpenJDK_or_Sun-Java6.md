---
title: "OpenJDK or Sun-Java6 ?"
date: 2009-05-19
forum: General Help
---

### Post by ActiveFrost on 2009-05-19
Had a problem with installing sun-java6-(bin/jre/jdk/plugin) on 8.04 LTS, and .. I installed 9.04.
Now, update contains OpenJDK, and I'm quite stressed about what should I do ( to remove OpenJDK or not ). 
What's your experience and what you would vote for ( actually, you CAN NOT skip this pool :D ) ?

---

### Post by Soul-Sing on 2009-05-19
openjdk en the ice tea plugin are fine.
some programms need(s) sun java: vuze/frostwire/etc.
but the open source java is really good.

---

### Post by kostkon on 2009-05-19
You can have many JVMs in your system, you don't necessarily need to remove OpenJDK, for example. You just need to set one of them to be the default JVM. You can do it by opening a terminal and giving
```
sudo update-alternatives --config java
```
and following the prompts.

You can at any time change the default JVM, of course.

Some more info [here]("https://help.ubuntu.com/community/Java").

---

### Post by medication on 2010-01-26
> **kostkon said:**
> You can have many JVMs in your system, you don't necessarily need to remove OpenJDK, for example. You just need to set one of them to be the default JVM. You can do it by opening a terminal and giving
```
sudo update-alternatives --config java
```


Great tip... not sure how I missed this config option before, but thanks so much.

---

### Post by karmila on 2011-05-02
> **kostkon said:**
> You can have many JVMs in your system, you don't necessarily need to remove OpenJDK, for example. You just need to set one of them to be the default JVM. You can do it by opening a terminal and giving
```
sudo update-alternatives --config java
```and following the prompts.

You can at any time change the default JVM, of course.

Some more info [here]("https://help.ubuntu.com/community/Java").

Thanks, I have been search for this :KS

---

