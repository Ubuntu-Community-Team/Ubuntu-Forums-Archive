---
title: "Windows emulation/replication..."
date: 2005-11-21
forum: Desktop Environments
---

### Post by xelink on 2005-11-21
This is my first post and I am new to linux in general, though not as sad as potentially possible.

I am essentially looking to run two programs off of Ubuntu, Photoshop CS and possibly Steam. I am running dual boot with windows XP-pro on my other hardrive. I am using the 32bit version insteed of the x86_64 because there appears to be greater compatability with... well everything...

What I thought would be my first step would have been to get WINE running to at the very least get a base started. I am having dificulty though. I have tried sevetal downloads... but each have the same net result...
 I even googled for answers specific to ubuntu and not just debin...

[[IMG]http://img295.imageshack.us/img295/3530/screenshot5xf.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshot5xf.png)


tell me if there is anything I am doing "wrong" or anything which I should do or add to this post

---

### Post by 23meg on 2005-11-21
You can install wine by typing ```
sudo apt-get install wine
``` at the terminal.

---

### Post by Zeroedout on 2005-11-21
[quote=xelink]This is my first post and I am new to linux in general, though not as sad as potentially possible.

I am essentially looking to run two programs off of Ubuntu, Photoshop CS and possibly Steam. I am running dual boot with windows XP-pro on my other hardrive. I am using the 32bit version insteed of the x86_64 because there appears to be greater compatability with... well everything...

What I thought would be my first step would have been to get WINE running to at the very least get a base started. I am having dificulty though. I have tried sevetal downloads... but each have the same net result...
 I even googled for answers specific to ubuntu and not just debin...

[[IMG]http://img295.imageshack.us/img295/3530/screenshot5xf.th.png[/IMG]]("http://img295.imageshack.us/my.php?image=screenshot5xf.png")


tell me if there is anything I am doing "wrong" or anything which I should do or add to this post[/quote]

For steam, i'de use the latest version of wine at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) . Just add the repos and it will making installing it easy. For Photoshop, i do not think it will work in regular wine, so perhaps try crossoveroffice. [http://www.codeweavers.com/](http://www.codeweavers.com/) .

---

### Post by xelink on 2005-11-21
Thank you to both of you, it is much appreciated. I will do some or all of that tomorrow... if not tonight. 

just curious though, i heard somewhere that windows scans your registry for WINE components and disables automatic updates/downloads from them. Any way around this?


EDIT:
=======================
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
chris@ubuntu:~$
=======================

any help?

---

