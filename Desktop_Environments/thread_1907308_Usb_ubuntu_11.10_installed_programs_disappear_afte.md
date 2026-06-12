---
title: "Usb ubuntu 11.10 installed programs disappear after restart"
date: 2012-01-11
forum: Desktop Environments
---

### Post by gtanmay on 2012-01-11
i installed ubuntu 11.10 on my 2GB pendrive it was fine and also running fine
and installed some programs like avg n vlc 

when i restarted pc (used windows 7) i removed pendrive
then again plugged in to boot from it
then my ubuntu was like a fresh install
programs n passwords were disappeared

what should i do???

---

### Post by deathkarr on 2012-01-11
hello gtanmay. It sounds like you've tried to use more space then what you actually have on the pendrive. I have had similar problems occur on my virtual machines when i used all the space for remastersys. Upon restart the machine would behave like a fresh install with no passwords or available user accounts to log into. Just went looking around and most people reckon 10gb of space is good. 

Here is a softpedia site for the wubi installation. [http://news.softpedia.com/news/Install-Ubuntu-from-Windows-in-3-Steps-Without-Using-a-CD-61304.shtml ]("http://news.softpedia.com/news/Install-Ubuntu-from-Windows-in-3-Steps-Without-Using-a-CD-61304.shtml")

Hope This helps

---

### Post by C.S.Cameron on 2012-01-11
Welcome to the forums.
If you use usb-creator, which comes on the Live CD, (and as usb-creator.exe on the iso for use in Windows), there is an option for persistence.
Max persistence using the casper-rw file is 4GB as set by FAT32. A 2GB pendrive will allow about 1.25GB persistence, enough to save settings and a few applications.

---

