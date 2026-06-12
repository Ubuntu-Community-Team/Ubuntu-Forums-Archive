---
title: "grammar browser - help installing"
date: 2010-09-20
forum: Desktop Environments
---

### Post by tora201 on 2010-09-20
Hello, just wondering if anybody knows how to install Grammar Browser in Ubuntu. (Using 10.04, 64-bit)

[http://linux.softpedia.com/get/Text-Editing-Processing/Others/Grammar-Browser-36564.shtml]("http://linux.softpedia.com/get/Text-Editing-Processing/Others/Grammar-Browser-36564.shtml")

Ah, and there are instructions in the above link, but can't follow them which is why I am asking for advice. 

Finally, wondering if there are any similar programs. Thanks!

---

### Post by tora201 on 2010-09-22
bumping this one.... see if anybody out there has any ideas.

---

### Post by adit on 2010-09-22
You need to install java runtime environment first.  Then extract the file grammarbrowser-1.3.0-20081101.zip into a directory named **grammarbrowser-1.3.0-20081101**.  This directory contains 5 subdirectories:

1)bin
2)grammar
3)laf
4)lib
5)META-INF

Navigate to the subdirectory "lib".  There you will find 3 files.
1) grammarbrowser.jar
2) grammarbrowser-runnable.jar
3) stanford-parser.jar
```
java -jar grammarbrowser-runnable.jar
```
I tested the above code in my computer.  A GUI window opens and the program runs.

---

### Post by tora201 on 2010-09-22
thanks man! Damn, why didn't I figure that one out? Cheers for your kind help

---

