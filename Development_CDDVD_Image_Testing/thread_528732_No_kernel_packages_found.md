---
title: "No kernel packages found"
date: 2007-08-18
forum: Development CD/DVD Image Testing
---

### Post by kingcharles1666 on 2007-08-18
During the command line install of the daily (18-08) of the gutsy alternate cd the installer comes with the message "no kernel packages found"
It happends after installing the base system.
I also tried the oem and text mode install and all with the same results. the CD checks out and the md5 was ok.
Any ideas?

thanks charles

---

### Post by Jukka-Pekka on 2007-08-18
I have the same problem with the daily build of today, and of yesterday.
(This did not happen with tribe-4 install)
Jukka

---

### Post by kingcharles1666 on 2007-08-18
the packages are there because i used a Feisty CD to do the basic install and did a CDROM distribution upgrade from the same CD and this worked fine. Gutsy loaded with the correct kernel (2.6.22-9)
So I guess there is an issue with the installation script.
I also noticed that it was initializing the floppy loader which seems strange. perhaps related?

---

