---
title: "Samsung PS/2 mouse not working after install"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Sef on 2005-12-28
I installed 5.10, Breezy on my friend's laptop: Compaq Presario 1200.  The only problem that I have fountd is that his Samsung PS/2 mouse does not work.  It works fine with windows.   What can I do to get his mouse working?

---

### Post by dcstar on 2005-12-28
[QUOTE=Sef]I installed 5.10, Breezy on my friend's laptop: Compaq Presario 1200.  The only problem that I have fountd is that his Samsung PS/2 mouse does not work.  It works fine with windows.   What can I do to get his mouse working?[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

---

### Post by Sef on 2005-12-29
The mouse still does not work after the reconfiguration.  What else can I try?

Thank you for the suggestion.

---

### Post by _oP on 2005-12-29
hello, 
u could try to change the bios option "mouse control (BIOS/OS)",
don` t worry this will not influence ur windows.  After i compiled my own Debian Kernel 2.6, i had the same problem. 

Good luck,

_oP

---

### Post by Sef on 2005-12-29
Problem solved: another friend had an extra usb mouse and it works.  Thanks for the suggestions.

---

