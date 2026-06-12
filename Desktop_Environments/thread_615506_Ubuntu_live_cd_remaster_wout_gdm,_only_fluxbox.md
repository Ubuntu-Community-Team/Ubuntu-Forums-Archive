---
title: "Ubuntu live cd remaster w/out gdm, only fluxbox"
date: 2007-11-17
forum: Desktop Environments
---

### Post by fibuntu on 2007-11-17
Hi!

I'd like to remaster the Ubuntu gutsy live cd so that I had only fluxbox as window manager (no gdm, no gnome). I've tried it with the LiveCDCustomization guide on the ubuntu wiki. First, I uninstalled all the dependencies of the ubuntu-desktop metapackage. Then I installed the fluxbox package and its dependencies. I finished the ISO, but, when I booted it with qemu, I got the usplash, but after a while it had gone and I had only a command line with some information of built-in shell, busybox and so on. So, how I could make the default livecd user login automagically and start fluxbox without gdm?

---

### Post by aysiu on 2007-11-17
I think to have an autologin at the GUI, you need some kind of display manager. If you don't like GDM, try WDM--it's lighter.

---

### Post by fibuntu on 2007-11-18
Thanks for reply. I would also want to remove all the gnome stuff from the live cd because i am gonna put fluxbox on it. So, what would be the safest way to do this so that I don't remove anything essential?

---

### Post by aysiu on 2007-11-18
> **fibuntu said:**
> Thanks for reply. I would also want to remove all the gnome stuff from the live cd because i am gonna put fluxbox on it. So, what would be the safest way to do this so that I don't remove anything essential?
Why don't you modify the Fluxbuntu CD instead? It might be less work.
[http://wiki.fluxbuntu.org/index.php?title=Get](http://wiki.fluxbuntu.org/index.php?title=Get)

---

### Post by fibuntu on 2007-11-19
> **aysiu said:**
> Why don't you modify the Fluxbuntu CD instead? It might be less work.
[http://wiki.fluxbuntu.org/index.php?title=Get](http://wiki.fluxbuntu.org/index.php?title=Get)

They seem to have currently only the gutsy RC on their servers (no live cd, only installer). So, what should I try? Maybe "apt-get remove --purge gnome*" or something like that?

---

### Post by utUtu on 2007-11-19
> **fibuntu said:**
> They seem to have currently only the gutsy RC on their servers (no live cd, only installer). So, what should I try? Maybe "apt-get remove --purge gnome*" or something like that?

It's a live CD plus an install option if you chose to.

:guitar:

---

### Post by angryfirelord on 2007-11-20
You could also grab an Ubuntu server cd and work your way up, rather than taking a regular Ubuntu CD and stripping it down.

---

### Post by fibuntu on 2007-11-20
So, heres what I'm gonna do:
1. Install ubuntu server on a partition.
2. Then install x, fluxbox, and any other software I want.
3. Then I configure the system the way I want (maybe autologin and automatically starting xserver)
4. Now for the interesting part. Couldn't the installed server partition be squashfs'ed?
5. Then I grab the desktop live image and replace the squashfs on it with my own. So, could it be that easy? :guitar:

There's still some disadvantage in this method. Because the squashfs is a normal install it doesn't have the same autoconfig scripts that the original live squashfs has. Or am I wrong? Well, that isn't my biggest problem.

---

### Post by Ptero-4 on 2007-11-27
> **fibuntu said:**
> So, heres what I'm gonna do:
1. Install ubuntu server on a partition.
2. Then install x, fluxbox, and any other software I want.
3. Then I configure the system the way I want (maybe autologin and automatically starting xserver)
4. Now for the interesting part. Couldn't the installed server partition be squashfs'ed?
5. Then I grab the desktop live image and replace the squashfs on it with my own. So, could it be that easy? :guitar:

There's still some disadvantage in this method. Because the squashfs is a normal install it doesn't have the same autoconfig scripts that the original live squashfs has. Or am I wrong? Well, that isn't my biggest problem.

Hi. I followed the LiveCDCustomization guide and have modded and remade the squashfs image, but I got a question now. How do I mod the LiveCD environment itself (remove gnome and put fvwm-crystal)?

---

