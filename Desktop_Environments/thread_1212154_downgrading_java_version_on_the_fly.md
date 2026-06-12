---
title: "downgrading java version on the fly"
date: 2009-07-13
forum: Desktop Environments
---

### Post by jjunos on 2009-07-13
Hello all,

I was wondering if there's a way to add a java version to update-java-alternatives.

I currently need both java 1.4.2 and Java 6 for two seperate projects, but flipping between the two is a hassle. I've set it up in my bashrc at the moment, but i know that:

/usr/bin/java -> etc/alternatives/java -> my java home

What i'd like is to (from reading online in a few places) do a

sudo update-java-alternative -s <javaversion>  

when i need java 1.4.2, or java 6. But whe ni do a

sudo update-java-alternative -l

I can only see my java 1.6. I manually installed the java 1.4.2 (since it's not in the repo). Idea's on how to add it to update-java-alternatives?


Thanks,
JJunos

---

### Post by Zorael on 2009-07-13
I know you can do it with the normal update-alternatives, not sure how you do it with update-**java**-alternatives.

```
$ sudo update-alternatives **--install** /etc/alternatives/java java /usr/lib/jvm/*java-version*/java **0**
```
Change the last integer to give it another priority when autodetecting which should be used, such as when calling it with **--auto** java.

List installed alternatives with 'update-alternatives **--list** java'. Set it with **--set**. And of course, spawn a menu with **--config**.
```
$ sudo update-alternatives **--set** java *<path to java executable added earlier, listed with --list>*
```
Omit sudo to make it a user-specific alternative.

If it gets botched up somehow (happens), just do '**--remove** java *<path to executable>*'. If it gets *really* botched up, manually edit **/var/lib/dpkg/alternatives/java**; Karmic seems to get stuff wrong on occasion, for one.

---

