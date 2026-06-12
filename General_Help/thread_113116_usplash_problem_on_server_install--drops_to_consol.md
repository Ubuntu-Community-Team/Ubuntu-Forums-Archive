---
title: "usplash problem on server install--drops to console on &quot;entering runlevel 2&quot;"
date: 2006-01-05
forum: General Help
---

### Post by whoisvince on 2006-01-05
How can I get Usplash to display the splash artwork all the way through the boot process?  

I'm running MythTV on an Ubuntu server install connected to a TV and need a little help getting usplash to behave.  I've installed usplash and did a dpkg-reconfigure linux-image-`uname -r` to get the splash screen going, and added vga=769 to /boot/grub/menu.lst to make the splash output play nicely with the refresh rate of my TV.  

Usplash comes up during boot exactly as it should with the Ubuntu logo and progress bar, but the usplash screen disappears when the boot process shows "* Entering runlevel 2" and the plain text console output is displayed instead of the splash screen until X loads.

Usplash has been added to runlevels S,1,2,3,4, and 5 according to sysv-rc-conf, and the symlinks are present and active in the /etc/rcX.d locations.  

I don't know much about Usplash, but I would appreciate any help.  Usplash runs perfectly on my laptop with a full install, but I would be thrilled to get in going on my MythTV box to have a more professional look.

---

