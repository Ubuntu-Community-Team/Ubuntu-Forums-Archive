---
title: "to install bzflag"
date: 2005-01-31
forum: Gaming &amp; Leisure
---

### Post by lycos on 2005-01-31
hi guys, :)
i began to use ubuntu 2 days ago.
before it, i was using "mandrake".
the tank battle game "bzflag" is coming with it.
and i love it very much.
but it is not coming with ubuntu.
i tried to install it but i couldnt.
first downloaded the rpm file and then genareted the .deb file using alien.  8-[ 
then installed it but didnt work. :confused: 
also it is writing at the bzflag web page "it is unstable".
any idea how to install and run it.
thanks for your time.

---

### Post by durianking on 2005-01-31
Why bother convert from .rpm to .deb as Ubuntu has its native .deb package.

Just do an apt-get install bzflag will install it for you automatically.

---

### Post by ericsp on 2005-01-31
... and if you want to install version 2, use the backport project: [http://ubuntu-bp.sourceforge.net/](http://ubuntu-bp.sourceforge.net/)

Eric

---

### Post by lycos on 2005-01-31
thanks for the super fast replaying :)
i wrote apt-get install bzflag as you can see below.
but something is wrong :(

root@ubuntu2:~ # apt-get install bzflag
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package bzflag
root@ubuntu2:~ #

what should i do now? :???:

---

### Post by jdodson on 2005-01-31
[QUOTE=lycos]thanks for the super fast replaying :)
i wrote apt-get install bzflag as you can see below.
but something is wrong :(

root@ubuntu2:~ # apt-get install bzflag
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package bzflag
root@ubuntu2:~ #

what should i do now? :???:[/QUOTE]

read this guide on how to enable universe repositories: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by lycos on 2005-01-31
i couldnt see any chapter like how to enable universe repositories?
maybe you can tell me what does the warning message mean "E: Couldn't find package bzflag"  :wink:

---

### Post by jdodson on 2005-01-31
[QUOTE=lycos]i couldnt see any chapter like how to enable universe repositories?
maybe you can tell me what does the warning message mean "E: Couldn't find package bzflag"  :wink:[/QUOTE]

sorry, my fault.  you are looking for the "add extra repositories" section:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by lycos on 2005-01-31
no problem  O:) 
i read the link and managed to install it :) correctly..
and now when i started it , the warning messages below is showing up.

root@ubuntu:~ # bzflag
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Could not set Video Mode: Couldn't find matching GLX visual.
Error creating window - Exiting
root@ubuntu:~ #

anyone has any idea about it?  :-?

---

### Post by lycos on 2005-01-31
i also have some nvidia drivers installed.
you can see here 
[imagefile](http://www.geocities.com/saimaktay/EkranGoruntusu.png) 
and my card is nvidia mx400.
thanks for your help :)

---

### Post by jdodson on 2005-01-31
[QUOTE=lycos]i also have some nvidia drivers installed.
you can see here 
[imagefile](http://www.geocities.com/saimaktay/EkranGoruntusu.png) 
and my card is nvidia mx400.
thanks for your help :)[/QUOTE]

did you run the command "sudo nvidia-glx-config enable" and then restart your machine?

---

### Post by lycos on 2005-01-31
thanks alot
i fixed the problem (ubuntuguide.com;glx) just before you wrote the messege :)
thanks a lot for your help guys. =D>

---

