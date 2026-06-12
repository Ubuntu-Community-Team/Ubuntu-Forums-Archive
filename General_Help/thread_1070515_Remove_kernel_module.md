---
title: "Remove kernel module"
date: 2009-02-15
forum: General Help
---

### Post by darrelljon on 2009-02-15
I tried to install virtualbox and following an error message tried to sudo apt-get install virtualbox-ose module. Anyway, the next reboot, I've lost my sound and my wireless. How do I restore them, I've tried sudo rmmod virtualbox-ose module but it doesn't seem to have worked. I'm using a live CD at the moment and if all else fails, I can backup my home and do a complete reinstall, but is there an easier way? Blacklist a module perhaps?

---

### Post by darrelljon on 2009-02-20
Used ubuntu recovery mode with an older kernel (accessed via grub) for the time being and audio and wireless are working.

---

### Post by Embiggens on 2009-02-20
Hmm, that almost sounds like something similar I just dealt with with VMWare.  I had to rmmod my usb 2.0 module to get my zune working with that, and on next re-boot had hardware interface issues with my ethernet and video.  Did you try "depmod -a <sound modules>" or anything like that?  Because in my case it seems like my module dpendencies got messed. I don't know offhand what the key sound modules are... maybe 'soundcore' for one.

---

