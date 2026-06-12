---
title: "[SOLVED] I broke it!!! Gnome Display Manager FAIL"
date: 2008-09-02
forum: Desktop Environments
---

### Post by heatpumpcontrol on 2008-09-02
Hello,

I had installed Cairo and during the process I made a change I didn't like to I reinstalled it. The undesired settings remained so I gksudo nautilus to remove all references to Cairo. Rebooted and that was the last time I saw my desktop.... lol

On boot I get the following:
kinit-name_to_dev_t(/dev/disk/by-uuid/...(disk id--my swap partition)
kinit-trying to resume from /dev/disk/by-uuid/...(same as above)
kinit-no resume image- doing a normal boot
loading img sdb7-not found
gnome start fail


I've done"
sudo /etc/init.d/gdm stop -> result is OK
sudo /etc/init.d/gdm start -> result is fail
sudo /etc/init.d/gdm stop 
startx -> result is black screen with lines and only way out is to CTL+ALT+DEL 2x

reconfigure gdm no help

After different attempts I'm now I'm getting a 
FreeFontPath: FPE"/usr/share/fonts/x11/misc" refcount is 2, should be 1; fixing

also I keep getting:
dpkg: serious warning: files list file for package 'libcairo2' missing, assuming package has not files currently installed.
---->same for the following 

libcairo2-dev, python-cairo, python-cairo-dev, libcairomm-1.0-1, libmono-cairo1.0-cil, libmono-cairo2.0-cil, libcairo-perl

Any help please..... I'm lost.

Miguel

---

### Post by heatpumpcontrol on 2008-09-03
OK, Thanks to no one in the community, I fixed it.... 

Copied over all the 'cairo' files from another pc into their respective locations and 'x' started.. no I have no sound but that's the least of my worries.....


Thank you everyone.

---

