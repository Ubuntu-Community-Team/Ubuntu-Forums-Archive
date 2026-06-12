---
title: "Beautifying aMSN goes wrong"
date: 2006-06-22
forum: Desktop Environments
---

### Post by [Nirvana] on 2006-06-22
alright, I compile tcl/tk 8.5 from CVS with no probs. I used [this thread]("http://www.ubuntuforums.org/showthread.php?t=75276") to install amsn CVS, and built the package. There were no errors throughout the whole thing. Now, when I try to sign in, I get an error about amsn needing tls in order to sign in. I have the pkg tcltls installed from apt, and I tried selecting my architecture and download it (which failed, btw). I even tried removeing and --purging amsn and tcltls, and reinstalling, but still no dice. What can I do?

error screen: [[IMG]http://img62.imageshack.us/img62/9573/amsnprob4sf.th.png[/IMG]](http://img62.imageshack.us/my.php?image=amsnprob4sf.png)

also, if anyone knows a good amsn + antialiasing guide for Dapper, feel free to hook me up.

---

### Post by [Nirvana] on 2006-06-23
Alright, I [found a thread]("http://www.ubuntuforums.org/showthread.php?p=1173063#post1173063"), but the link to aMSN was down :(

If anyone has a copy, upload to: [http://halovids.globalnetworld.com/upload](http://halovids.globalnetworld.com/upload)

---

### Post by [Nirvana] on 2006-06-23
*bump* from 4th page to the first :P

---

### Post by panurge77 on 2006-06-23
sudo gedit /usr/lib/tls1.50/pkgIndex.tcl

and then change the line
if needed tls 1.5
to
if needed tls 1.50

Yes. Just add the zero. Dumb thing, huh? I dont know why they dont fix this in tcl8.5
(You may also need to tell amsn in option>advanced that tls is in /usr/lib)

---

### Post by [Nirvana] on 2006-06-25
no dice.

I installed neto's tcl/tk pkgs, then used [this](http://www.ubuntuforums.org/showthread.php?t=75276) guide to get CVS aMSN, installed that, changed to the 1.50, but still nothing.

---

