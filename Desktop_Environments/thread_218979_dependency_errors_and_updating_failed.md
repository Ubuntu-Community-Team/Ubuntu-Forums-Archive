---
title: "dependency errors and updating failed"
date: 2006-07-19
forum: Desktop Environments
---

### Post by munro on 2006-07-19
Okay, I got Ubuntu 6.06 exactly 1 week ago and I have 28k dialup. I have to go to the library just to get a file 1 mb big. Anyway, I am trying to get mp3 support and DVD playback. I have downloaded everything and tried to install them. Okay, I installed everything but 4 files that I need. Each time, I get a error, 

"Dependency is not satisfiable: libc6"

I downloaded 'libc6_2.3.2.ds1-22sarge3_i386.deb' and when I try to install it, it says that I have a newer version installed. How do I update 'libc6' or get those errors to not come back?

I am new to linux, so be gentle:-? 

-A. Munro

---

### Post by ThrobbingBrain66 on 2006-07-19
libc6 is installable from the repositories (the newest version is 2.3.6).  I suggest running 
```
sudo aptitude install libc6
```
from a terminal or installing it through synaptic.  If that doesn't work, type 
```
sudo gedit /etc/apt/sources.list
```
and post the output here.  You may have to enable some extra repositories.

---

### Post by munro on 2006-07-19
That'd be nice, but the computer that I have ubuntu dosen't have an internet connection and I cannot connect it to the internet. Is there a manual download file?

-Thanks
A. Munro

---

### Post by philippe_carlo on 2006-07-19
Seems like you downloaded a debian sarge package. Debian has a more conservative packaging strategy than ubuntu, so the version of that libc6 may be an old one. You probably needed the newer one from the ubuntu archives. On my machine (fully up-to-date of course) I have 2.3.6 installed. So, you probably need that one too. 

It's right [Here]("http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.6-0ubuntu20_i386.deb")

---

### Post by munro on 2006-07-19
Thank you!!!!!1 Downloading it now on 28k dialup... It'll be about an hour. Thanks again!!!

---

