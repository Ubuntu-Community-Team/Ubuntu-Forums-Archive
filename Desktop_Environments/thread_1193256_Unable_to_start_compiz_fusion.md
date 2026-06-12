---
title: "Unable to start compiz fusion"
date: 2009-06-21
forum: Desktop Environments
---

### Post by Arthas168 on 2009-06-21
The message i got in terminal was:

pubuntu@pubuntu:~$ compiz --replace
Checking for Xgl: Xlib:  extension "XVideo" missing on display "10.0.2.2:0.0".
xvinfo: No X-Video Extension on 10.0.2.2:0.0
not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
FATAL: Module battery not found.
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks

Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display '10.0.2.2:0.0'.

I was first not able to start compiz fusion after installing via add/remove. When i put extra on visual effects on appearances, a pop up box appears saying the composite extension is not available. I typed in compiz --replace in terminal to start it and the above appeared without compiz working.

Can anyone help me please. I'm a complete linux beginner having started only 2 days ago.

---

### Post by Arthas168 on 2009-06-21
Ive just run compiz check using the commands in [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check). The output was:

pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   Unknown
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
 Graphics chip:         Unknown
 Driver in use:         SKIP
Xlib:  extension "XVideo" missing on display "10.0.2.2:0.0".
xvinfo: No X-Video Extension on 10.0.2.2:0.0
 Rendering method:      SKIP

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to locate your Xorg log 

I hope this helps you help me.

---

### Post by Arthas168 on 2009-06-21
Bump

---

