---
title: "Not Loading up Desktop (Gnome)"
date: 2007-11-26
forum: Desktop Environments
---

### Post by chamakits on 2007-11-26
Hey guys, yesterday I was downloading a few things from the repository.  I'm pretty sure these things weren't critical in any way, but they might have caused this, so, just thought I'd mention it.  Anywho, after a while, gnome started acting up.  The nm-applet began telling me it had an error, but it didn't disconnect me from the network.  The Applications Places and other tabs wouldn't work properly, when clicked they would pull down showing the options, then act as if it had been reclicked, so needless to say it was bothersome to pick anything from the menus, and to top it off, not everything showed up.  Eventually, I restarted the computer.  In the next boot up, gnome wouldn't start.  It goes straight to the terminal, showing the following:

Starting up...
Loading, please wait...
usplash:  Setting mode 1280x1024 failed
usplash:  Setting mode 1152x864 failed
usplash:  Using mode 1024x768
kinit:  name_to_dev_t(/dev/disk/by-uuid/4d72f958-6c1e-4852-9593-f64e11a2d116) = sda2(8,2)
kinit:  trying to resume from /dev/disk/by-uuid/4d72f958-6c1e-4852-9593-f64e11a2d116
kinit:  No resume image, doing normal boot...

Ubuntu 7.10 LinuxChamakits tty1

LinuxChamakits login:
Ubuntu 7.10 LinuxChamakits tty1

LinuxChamakits login:



Any other information I can give you to be more specific, or anything, please do tell.  Thanks in advance!


PS:  I can start xcfe with startx, but nothing more.  Any thanks would be appreciated.

---

### Post by paranoiahax on 2008-01-07
hmm i'm experiencing something similar to this, I load grub as usual, select ubuntu, and it goes to the usplash screen, and loads marginally (like a bar of orange can be seen right at the beginning) but freezes. I check what's going on by pressent alt trl f1 and I get this:

> Starting up...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768


and it just stays there and doesn't do anything, so i have to hold down my power button until i restart my computer. i reckon it has something to do with my grub, because i have been changing and adding stuff to my grub recently, and it's done this before. so i chmod my grub directory to wr-r--r-- (644 i believe) and it's worked before, but this time it's not working. has anyone got any ideas? 

(btw sorry to steal your thread chamakits, i'll post a new one if you like)

thanks in advance, Para

---

