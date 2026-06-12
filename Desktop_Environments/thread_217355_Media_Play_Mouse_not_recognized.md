---
title: "Media Play Mouse not recognized"
date: 2006-07-17
forum: Desktop Environments
---

### Post by mect on 2006-07-17
So the mouse works like a normal mouse.  I tried to install lmpc using [HTML]http://daemon.prozone.ws/~david/projects/lmpcm_usb/[/HTML] and [HTML]http://www.ubuntuforums.org/showthread.php?t=65471&page=14&highlight=mediaplay[/HTML]
everything appears to run fine until I check it using:
# dmesg | grep '^lmpcm.* usb'
I don't get anything back, which the tutorial indicates means that the mouse isn't recognized.  I've double checked that it isn't getting stolen by usbmouse or usbhid (neither can be removed).  I've restarted the computer and tried again.  Does anyone have any ideas what could be wrong.  I installed kernel 2.6.17, checked that the appropriate modules are in the .config file.  This is for lmpcm_usb-0.5.4.    Thanks in advance for any help.

edit-and I'm using Kubuntu dapper

---

