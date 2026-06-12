---
title: "How to install and run Google Refine"
date: 2011-07-14
forum: Education &amp; Science
---

### Post by kimberlite on 2011-07-14
Hi there,

Is there anybody using Google Refine app on Ubuntu (my distro is 10.10 M&M)?
I have followed the instruction [here]("http://code.google.com/p/google-refine/wiki/InstallationInstructions") and the application has not started in default browser. Did I miss a point? I've also try to get direction from ./refine -h, but it was rather confusing..., at least for me.

Cheers,

Kimberlite

---

### Post by kimberlite on 2011-07-14
Some additional info:
```
$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Server VM (build 19.1-b02, mixed mode)
```
Anyhow, I have not encountered any problem when I am using Java based applications.

I've found GRefine's mailing list, but I could not identified any relevant post for my issue. Strange ...

---

### Post by kimberlite on 2011-07-15
I do not really no the reasons, after restarting my computer _at office_ today it just started fine, so I will mark this thread as SOLVED.


```
./refine 
Starting Google Refine at 'http://127.0.0.1:3333/'

13:43:13.306 [            refine_server] Starting Server bound to '127.0.0.1:3333' (0ms)
13:43:13.308 [            refine_server] Max memory size: 1024M (2ms)
```
...
EDIT:
It turned out that $http_proxy was not correctly set _at home_. However, I am still have not understood why I have to set this variable differently from the so called "system-wide" setting (cf. network-manager). Thanks for the hints for google refine forums that I finally managed to find: [http://code.google.com/p/google-refine/issues/detail?id=262]("http://code.google.com/p/google-refine/issues/detail?id=262")

---

