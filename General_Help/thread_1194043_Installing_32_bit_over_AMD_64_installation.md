---
title: "Installing 32 bit over AMD 64 installation"
date: 2009-06-22
forum: General Help
---

### Post by ggb-uk on 2009-06-22
I have installed, and been running for the last 6 months, ubuntu using the AMD64 kernel.

I am realising that there are far too many things that simply are not compiled for 64 bit (particularly multimedia stuff), and am thinking about installing the 32 bit kernel to improve compatibility.

Can I just install the 32 bit kernel as another kernel in Grub, or do I need to scratch the 64 bit installation?  In particular, I am loathed to wipe clean the disk, and with it everything else I have been doing for the last 6 months (the actual data can easily be copied, and copied back, but all the configuration will have to be reapplied, and that would be tedious).

I have 4GB RAM with an NVidia chipset (and am running NVidia RAID-1 on the hard disks).

Also, should I be using the ordinary 32 bit kernel, or 32 bit with extended memory?

With thanks,

George.

---

### Post by Cheesemill on 2009-06-22
You'll have to do a clean install of the 32-bit version.
 
You can make a backup of your /home folder and then restore it to the new install, this will keep all of your application settings intact (they're all stored in hidden folders in your home folder).
This is why people suggest you keep /home on a seperate partition, so you can reinstall without losing any of your data/settings.
 
Edit - Check out post #2 here
[http://ubuntuforums.org/showthread.php?t=576629](http://ubuntuforums.org/showthread.php?t=576629)
for a way to export all of your installed apps for easy re-installation

---

### Post by ggb-uk on 2009-06-24
Thanks, Cheesemill, that was what I feared.

Yes, I realise that I can back up the /home directory, but much of the rest of the configuration is in the /etc directory, and I will then have to go through and install (or uninstall) all of the packages that I presently have installed under AMD64.  It could take several days getting things back to where they are now, but if that is the only way (as I feared it would be), then i shall just have to wait until I think I have several days to do all of it.

George.

---

### Post by ggb-uk on 2009-06-24
Cheesemill,

I looked at your link for backing up the package list.  This at least will save some time, but the /etc directory will still be an issue.

I will also have to worry about the NVidia RAID-1 drivers which caused a few headaches when I first installed the system.

Thanks anyway,

George.

---

