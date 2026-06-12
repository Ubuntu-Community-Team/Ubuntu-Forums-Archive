---
title: "Triple Booting"
date: 2005-01-28
forum: Desktop Environments
---

### Post by justaguynpc on 2005-01-28
I know alot of us dual boot, I want to take it just 1 step further.  I currently have WinXP, and Slack 10.0 on my home PC, and have installed Ubuntu "Warty Wartog" on my laptop.  I use WinXP for a few games, guess you could call it my security blanket at this point in time.

I am really attached to Slack, only using KDE for the non-support of gnome in further updates.  I like what I see of Ubuntu and want it primarily for it's great Gnome DM.

How would I SUCCESSFULLY install Ubuntu along side my Slack / WinXP?  I am more than willing to re-install both OS's, rather than use some third party disk package to enable re-sizing of my hard-drive.  You see, I am using only one HD, and this I think shouldn't pose too big of a problem, or does it? Slack uses Lilo as it's bootloader, after installing Ubuntu, I see that it uses Grub,  so ........


justaguy

**Should this have been posted under "other Software Support?  (sorry!)**

---

### Post by DJ_Max on 2005-01-28
I'm not certain, but I think you can use Lilo. I saw a few post mentioning Lilo. Since Lilo is just another boot loader for the x86.

To triple boot, you would need to reinstall everything, and make space for 3 OS's.

---

### Post by justaguynpc on 2005-01-28
I am well aware of the re-install issue!   8-[

---

### Post by steffen on 2005-02-01
I think Ubuntu and Slack can use the same swap partition. So the only thing you need to do is to set up a new partition for the third operating system. Then you need to copy some of the startup files from your third OS into /boot and set up Lilo.

Don't know the exact workings of this, and which files you need in /boot, but I think that's the procedure.

---

