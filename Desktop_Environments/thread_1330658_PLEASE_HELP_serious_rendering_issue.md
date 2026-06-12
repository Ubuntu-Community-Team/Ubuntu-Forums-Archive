---
title: "PLEASE HELP: serious rendering issue"
date: 2009-11-18
forum: Desktop Environments
---

### Post by dapeaz on 2009-11-18
Screenlets appear as just boxes of color and the biggest problem, the menu bar in both kWord and OpenOffice show up as gray bars, along with all the options within them.  I'm really enjoying Ubuntu so far, but if it's a matter of graphics card, I need to know.

After running diagnostics, this is the result I got:
> 
Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)  			 		

---

### Post by utnubuuser on 2009-11-19
I had the same issue with Kubuntu 9.10.  Installing the ubuntu-desktop on top of Kubuntu solved it for me. 

9.10 doesn't create a xorg.conf file by default, but I believe you can still run > sudo dpkg-reconfigure xserver-xorg -phigh and then copy and paste the configurations for that card from an older version/install or find out what the configurations are supposed to be for your card and add them to the xorg.conf file

---

### Post by dapeaz on 2009-11-20
i searched the file system, and the only xorg.conf i could find was an archive in /usr/share/man/man5 that contains the file xorg.conf.5

Any ideas?

---

