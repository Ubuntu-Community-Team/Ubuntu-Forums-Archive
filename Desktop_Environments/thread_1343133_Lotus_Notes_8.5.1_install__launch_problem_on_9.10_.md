---
title: "Lotus Notes 8.5.1 install / launch problem on 9.10 karmic"
date: 2009-12-01
forum: Desktop Environments
---

### Post by anystupidname1 on 2009-12-01
Happy Holidays! Could anybody offer insight into this problem please?

Installing Lotus Notes 8.5.1 seems to have completed without error. However, when I try to run it, nothing happens. When I run it from terminal
> /opt/ibm/lotus/notes/framework/../notes %Fthis shows up:
> 
/opt/ibm/lotus/notes/framework/../notes: error while loading shared libraries: libgnomeprint-2-2.so.0: cannot open shared object file: No such file or directoryThis is on Karmic:
2.6.31-15-generic SMP x86_64

These packages are installed:
libgnomeprint2-ruby
libgnomeprint2-ruby1.8
libgnomeprint2.2-0
libgnomeprint2.2-data
libgnomeprintui2-ruby
libgnomeprintui2-ruby1.8
libgnomeprintui2.2-0
libgnomeprintui2.2-common
mozilla-browser
sun-java6-bin
sun-java6-jre
sun-java6-plugin
java-common

Also, does anybody know what the double dot in the path accomplishes? (just curious)

Any assistance would be much appreciated!

---

### Post by anystupidname1 on 2009-12-03
I finally found this:

[http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument)

---

### Post by Gman3025 on 2009-12-09
Does the problem solve?

---

### Post by anystupidname1 on 2009-12-11
Yes, the problem solves.

---

