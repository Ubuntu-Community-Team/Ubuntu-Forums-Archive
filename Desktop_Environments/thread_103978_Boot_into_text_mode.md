---
title: "Boot into text mode"
date: 2005-12-15
forum: Desktop Environments
---

### Post by vagmi.mudumbai on 2005-12-15
Hi,

First off, I need to thank you guys for the amazing work you are doing. I am planning to setup a lab for school children for an NGO. The NGO can currently obtain only old P2 or P1 machines with network connectivity and very low hard disk space. (few hundred mbs). I would like to load Ubuntu on those machines but the problem is that the X server is too slow. I have a much faster server and I wish that students telnet into that machine for their programming exercises.

For this i need to avoid installing the X server and GNOME related libraries and just install the basic text only operating system. Can you help me out with this?

Regards,
Vagmi

---

### Post by mcduck on 2005-12-15
sure, when starting installation, type 'server' and you'll get minimal install without X.

---

### Post by vagmi.mudumbai on 2005-12-15
Thanks a ton. Can you tell me the approximate size it would require? Also can Ubuntu work on P1 machines with 32 MB of RAM?

---

### Post by mcduck on 2005-12-15
I haven't done that myself, but Ubuntu wiki says you need 64MB of RAM and 500MB of hard disk space for server install, and 128MB RAM & 2GB HD space for desktop. [https://wiki.ubuntu.com/BreezyReleaseNotes]("https://wiki.ubuntu.com/BreezyReleaseNotes")

I have hoary installed on a AMD K6-2 @ 500MHz with 120MB of RAM, and it's usable, altough Gnome runs a bit slow. ;) XFCE works well. I wouldn't even try with 32MB of memory.

---

### Post by ludvig on 2005-12-21
Hi!

There are an other distribution that you could try.
Take a look here to see if it could be of interest:
[http://www.skolelinux.org/portal/](http://www.skolelinux.org/portal/)


regards
ludvig

---

