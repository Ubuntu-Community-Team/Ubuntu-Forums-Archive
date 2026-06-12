---
title: "Having trouble executing setup.jar to install UpToDate"
date: 2009-02-28
forum: General Help
---

### Post by hotweiss on 2009-02-28
I am trying to install UpToDate:

[http://www.uptodate.com/home/index.html](http://www.uptodate.com/home/index.html)

...on Ubuntu, but it does not work in wine nor through the java client. Oddly enough there is a Linux and Ubuntu directory even though there is no official support for UpToDate on Linux. The main directory has setup.jar and when I try to execute it I get this error:

> ./setup.jar: 1: Syntax error: ")" unexpected

There is also a file called setuplinux.sp that contains:

> is.debug=1

...in it.

The windows setup file also is java based and starts up showing me empty windows with no text in wine. Does anyone have a solution for me?

---

### Post by taurus on 2009-02-28
Isn't that a java app?

```
javac setup.jar
```
Assuming you have installed JDK first.

---

### Post by hotweiss on 2009-02-28
> **taurus said:**
> Isn't that a java app?

```
javac setup.jar
```
Assuming you have installed JDK first.

I have installed sun-java6-jdk and now I get this error:

> error: Class names, 'setup.jar', are only accepted if annotation processing is explicitly requested
1 error

---

### Post by hotweiss on 2009-03-01
bump

---

### Post by hotweiss on 2009-03-02
bump

---

### Post by martalli on 2009-03-31
I'm glad to see someone else is trying to install this, too.  I actually managed to install a previous version of UpToDate off the CD, but witht he last two releases can't figure it out.  The support staff wouldn't help, but they sent a cryptic message along the lines that "You will figure it out pretty easily".  Thanks guys =)

I am currently fiddling around with it, and will let you know.  I was under the impression that you should run a .jar file like this:
```
java -jar setup.jar
```
However, when I do this, I get:
```
martalli@nothung:~/download/utd$ java -jar setup.jar
Invalid or corrupt jarfile setup.jar
```
Hmmmm...

---

### Post by manudias on 2009-04-04
try the portable version:
it seems to be working on Ubuntu 8.10/Vista/XP

Megaupload

Parte 1
[http://www.megaupload.com/?d=CO5JHKAD](http://www.megaupload.com/?d=CO5JHKAD)
Parte 2
[http://www.megaupload.com/?d=XQSEV1AI](http://www.megaupload.com/?d=XQSEV1AI)
Parte 3
[http://www.megaupload.com/?d=44ZVWPE9](http://www.megaupload.com/?d=44ZVWPE9)
Parte 4
[http://www.megaupload.com/?d=O1CWM0CZ](http://www.megaupload.com/?d=O1CWM0CZ)
Parte 5
[http://www.megaupload.com/?d=BGCW5DX0](http://www.megaupload.com/?d=BGCW5DX0)


Rapidshare

Parte 1
[http://rapidshare.com/files/206984961/UpToDate_Portable.part1.rar](http://rapidshare.com/files/206984961/UpToDate_Portable.part1.rar)
Parte 2
[http://rapidshare.com/files/206985020/UpToDate_Portable.part2.rar](http://rapidshare.com/files/206985020/UpToDate_Portable.part2.rar)
Parte 3
[http://rapidshare.com/files/206985028/UpToDate_Portable.part3.rar](http://rapidshare.com/files/206985028/UpToDate_Portable.part3.rar)
Parte 4
[http://rapidshare.com/files/206985134/UpToDate_Portable.part4.rar](http://rapidshare.com/files/206985134/UpToDate_Portable.part4.rar)
Parte 5
[http://rapidshare.com/files/207013800/UpToDate_Portable.part5.rar](http://rapidshare.com/files/207013800/UpToDate_Portable.part5.rar)

---

### Post by manishmahabir on 2010-04-07
Do not download from above link...completely useless.
Try torrent instead.

---

### Post by manishmahabir on 2010-04-07
Has anybody been successful plz post how u did it...

---

