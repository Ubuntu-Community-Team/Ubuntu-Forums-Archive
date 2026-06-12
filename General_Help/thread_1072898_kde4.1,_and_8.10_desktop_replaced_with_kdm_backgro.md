---
title: "kde4.1, and 8.10 desktop replaced with kdm background"
date: 2009-02-17
forum: General Help
---

### Post by igor_nz on 2009-02-17
Hi all, I searched the forums and couldn't find someone with quite the same problem as I've run into.

I run 8.10 with KDE4.1 which has all been playing nicely untill yesterday. Now, when I start up KDM loads fine but when I attempt to log in I see my desktop for about 1 second after which it is replaced by the KDM background. At this point I can still bring Krunner up with alt-f2 and even run konsole (though it loads without window decoration) but other kde applications won't load. If I try to log into the "failsafe" from kdm the screens turns black for a second then brings me back to the log-in screen 

I hadn't played with any settings before this started but have since removed any compiz info from xorg.conf, uninstalled compiz and tried the "fix xorg" from  'recovery mode'. All to no avail. 

Anyone having any better ideas?
Thanks in advance

---

### Post by txcrackers on 2009-02-18
If it won't bother you, you *could* just blow away your current settings and essentially start with a clean slate (this has been recommended for the early 4.1 versions).

At the next boot, boot into "safe" mode, change to your home directory and *rm -rf .kde*

---

### Post by igor_nz on 2009-02-18
Thanks for that, as it happened I installed a bunch of updates that had been waiting to go from the command line and something in that obviously overwrote whatever had gone wrong, all running fine now.

Thought I'd post the reply in case anyone was googling for a similar problem (even if I used a pretty blunt tool to fix it)

---

