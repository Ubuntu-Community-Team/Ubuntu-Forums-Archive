---
title: "Is there 64bit version of flash?"
date: 2009-05-18
forum: Desktop Environments
---

### Post by carfield on 2009-05-18
I would like to remove all those 32bit libraries to make my computer all are 64bit binary. 

Flash is very essential for me as I like to watch youtube movie, but look like there is only 32bit version of flash, am I right? Or there is 64bit flash plugin somewhere in the internet?

---

### Post by Arup on 2009-05-18
> **carfield said:**
> I would like to remove all those 32bit libraries to make my computer all are 64bit binary. 

Flash is very essential for me as I like to watch youtube movie, but look like there is only 32bit version of flash, am I right? Or there is 64bit flash plugin somewhere in the internet?

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

Extract and move the libflashplayer.so to /usr/lib/mozila/plugin but make sure any previous flash and nsplugin is uninstalled via synaptic or sudo apt-get --purge remove method

---

### Post by carfield on 2009-05-21
Thx, just try, but it doesn't work....BTW, also try Gnash, it doesn't seen to working either :-/

---

### Post by oldos2er on 2009-05-21
Try [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by skullmunky on 2009-05-21
On Jaunty 64, I just looked for Flash in synaptic.  I installed "flashplugin-installer" and it worked fine.  (I don't know if that's a native 64bit plugin or if it's in a wrapper)

---

