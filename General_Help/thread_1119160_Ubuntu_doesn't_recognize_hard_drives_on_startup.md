---
title: "Ubuntu doesn't recognize hard drives on startup"
date: 2009-04-07
forum: General Help
---

### Post by jonathannevins on 2009-04-07
I just upgraded to Ubuntu 8.04 and I'm having a small problem.  When the OS first starts up, it doesn't recognize either of two hard drives.  Neither of them show up on the desktop, and any links to files on either drive do not work.  If I go into Nautilus, each drive is displayed on the left side, and as soon as I click on each of them they show up on the desktop, links work, and I can access them fine.  This is not that big of a problem, but a slight annoyance I would like to fix if possible.

Here is some info on my computer:
Ubuntu 8.04
AMD Athlon X2 4200+
Gigabyte GA-K8NF-9 Motherboard
1 GB Corsair XMS RAM (CMX1024-3200)

I don't remember exactly what model either hard drive is, but they are both Seagate drives.  One is connected through SATA II and one is IDE (I'm thinking this may have something to do with the problem).  The system boots off the SATA II drive, not the IDE drive.  The IDE drive jumper is set to "Slave," but I've tried setting it to "Master," and that does not fix the problem.  

Does anyone have any suggestions as to how I could fix this problem?

---

### Post by ivanvajar on 2009-04-07
Are HDDs listed under 'Places' menu?

---

### Post by jonathannevins on 2009-04-07
Yes, both drives show up in the "Places" menu when I start up Ubuntu.

---

### Post by Therion on 2009-04-07
> **jonathannevins said:**
> Yes, both drives show up in the "Places" menu when I start up Ubuntu.
That's good news; you're over the hump then. What you need to do, then, in order to get the drives to mount at startup, is add the mountpoints to your fstab.

Here's a slightly long-winded introduction to what that means and how to do it:

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

---

### Post by jonathannevins on 2009-04-07
Ok, I set the mount points of both drives to be the Desktop, and that has led to some new problems.

First, not only do icons for both drives show up, but the folders and files on my second drive also show up on the desktop.  

Second, when I try to access my first hard drive it displays the exact contents of my second drive, but it should be completely different.

Is there any way to stop the contents of my second drive from showing up on the desktop?  I want to keep the desktop as the mount point so that the drives show up in "Computer" and "Places." (Or is there a way to have them still show up in "Computer" and "Places" without the desktop being the mount point?)

In addition, can anyone explain why the contents of my second drive shows up when I try to access my first drive?  I think it may have something to do with the desktop being the mount point for both drives.

Thanks.

---

