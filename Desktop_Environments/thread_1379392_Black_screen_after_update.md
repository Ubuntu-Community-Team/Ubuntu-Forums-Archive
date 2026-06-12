---
title: "Black screen after update"
date: 2010-01-12
forum: Desktop Environments
---

### Post by kristensson.jonas on 2010-01-12
Hi!

I just recently updated my ubuntu 9.10 with the standard updates that pop up every once in a while. But after I rebooted the computer it won't load my desktop environment, it just gives me a black prompt screen where i can login. Can I just simply restart the desktop environment with some command (if so which one) or is there anything else I need to do to get it up and running again?
Anyone else who has got the same problem?

Regards
Jonas

---

### Post by quixote on 2010-01-13
Try logging in at the command line, and then once you have a prompt enter startx or restartx:```
your-user-name$ startx
```

If that does it, I'm not sure whether you should try to fix broken packages first, or just check for further updates and install those.  It can't hurt to ask for "fix broken packages" so try that first. (It's one of the menu items, but I don't remember which category it's under.)

If it refuses to start X, ie the graphical interface, you can type the same commands without it:```
sudo dpkg --configure -a  [to try to fix any errors]

sudo apt-get update  [to get the most recent versions in the repositories]

sudo apt-get upgrade [to upgrade to those recent versions]
``` 

Then reboot and cross your fingers. :?

---

### Post by sh4d0w808 on 2010-01-14
Similar happened to one of my colleagues yesterday, but his GRUB had been gone. He had to reinstall GRUB. I also saw similar problems on a hungarian ubuntu-site.

---

