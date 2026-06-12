---
title: "Wine does not find the latest JDK version ?"
date: 2014-11-29
forum: Desktop Environments
---

### Post by zn52 on 2014-11-29
hello,
I want to run an .EXE file which exists in the windows directory under Program files - It runs well under windows . but as I'm anti-windows, I wanted to execute it in ubuntu.
But I get the message : this application requires a java runtime environment 1.7.0_51 or higher
But in the terminal I have the latest :

java - version
java version "1.8.0_11"
Java(TM) SE Runtime Environment (build 1.8.0_11-b12)
Java HotSpot(TM) Server VM (build 25.11-b03, mixed mode)

How come it does not recognize the JDK version ?
thank you,

---

### Post by raketax on 2014-11-29
My first guess would be that you don't have a windows version of java installed on wine. Try to think of it as a separate virtual machine, you have java for linux but the poor windows program cannot see that in wine.

---

