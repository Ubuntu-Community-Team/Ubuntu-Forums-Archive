---
title: "Desktop Icons and File Associations Stopped Working"
date: 2007-12-21
forum: Desktop Environments
---

### Post by ryker on 2007-12-21
I'm having some weird issues all of a sudden with a fresh 64bit 7.10 Gutsy install.  Everything was working fine, and I noticed today that all of my files are no longer associated with any program.  So, I can't click on a .doc file and have it open in openoffice.  jpg doesn't launch anything, etc.
Also, my icons on the desktop and in the computer browser have disappeared and the text looks weird.
I have attached a screenshot.
Any ideas what is going on?
Thanks

[[IMG]http://img509.imageshack.us/img509/4887/screenshothw3.th.jpg[/IMG]](http://img509.imageshack.us/my.php?image=screenshothw3.jpg)

---

### Post by smartboyathome on 2007-12-21
Hm... looks like some nautilus file got replaced/deleted in your home directory which defines which files get opened with what program. I would start up the livecd, and then see if there are any differences between the ~/.nautilus directories on your install and the live system.

---

