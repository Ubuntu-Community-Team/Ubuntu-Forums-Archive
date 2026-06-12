---
title: "32 bit with 64 bit  java rts"
date: 2012-06-02
forum: Desktop Environments
---

### Post by forsubhi on 2012-06-02
I installed 32bit java rts on 64 bit ubuntu and I get the following error when I run it 

```
subhi@subhi-pc:/media/93638ab5-2de5-4fac-9c07-24d4fc86b7ae/programs/java/RealTime/JavaRTS-2.2-fcs-tmp/jrts-2.2_fcs/bin$ ./java -version
dl failure on line 824Error: failed /media/93638ab5-2de5-4fac-9c07-24d4fc86b7ae/programs/java/RealTime/JavaRTS-2.2-fcs-tmp/jrts-2.2_fcs/jre/lib/i386/server/libjvm.so, because libcap.so.1: wrong ELF class: ELFCLASS64
```

is it possible to solve this problem ? 
and is it possible to get 64 bit java rts ?

---

### Post by Paddy Landau on 2012-06-03
32-bit programs usually do not work on the 64-bit operating system.

According to [Sun's evaluation page]("http://java.sun.com/javase/technologies/realtime/rts/"), a 64-bit is indeed available. Install it instead.

---

### Post by forsubhi on 2012-06-03
I get this message 

 The Java Real-Time System evaluation program is closed at this time.

[http://www.javelinfeedback.com/sun/index.jsp?pi=859927bc085603aa66e68ca214edfb6c&download=x86linux-90days&V=2.2-64bit](http://www.javelinfeedback.com/sun/index.jsp?pi=859927bc085603aa66e68ca214edfb6c&download=x86linux-90days&V=2.2-64bit)

what is the problem?

---

### Post by Paddy Landau on 2012-06-04
> **forsubhi said:**
> The Java Real-Time System evaluation program is closed at this time. ... what is the problem?
You'll have to ask Sun that question, unfortunately. I suggest you ask Sun how to get hold of the 64-bit version.

---

### Post by inashdeen on 2012-06-04
I found a 64 bit java here.[ http://www.java.com/en/download/manual.jsp]("http://www.java.com/en/download/manual.jsp")

is this what you need

---

