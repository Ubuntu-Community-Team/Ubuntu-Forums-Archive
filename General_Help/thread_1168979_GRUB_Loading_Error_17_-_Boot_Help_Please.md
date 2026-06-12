---
title: "GRUB Loading Error 17 - Boot Help Please?"
date: 2009-05-24
forum: General Help
---

### Post by apocalex13 on 2009-05-24
[COLOR=#333333]Okay so here's what I've done:

1. Got a laptop with Vista 32bit Home Pre.
2. Installed Ubuntu 8 and dual-booted with Vista using the GRUB boot manager (no problems, has been working for 2 months)
3. Attempted to install windows XP as well, but the installation process gave me a Blue Screen, so I stopped trying
4. Now the "GRUB Loading stage1.5" returns the error "GRUB loading, please wait... Error 17"

The boot manager no longer comes up, and I can't get GRUB to boot. I've tried reusing my Ubuntu iso disk and selecting boot from disk under boot options, but all it does is give the message:[/COLOR]
[COLOR=#333333][/COLOR] 
[COLOR=#333333]"ISOLINUX 3.63 Debian-2008-07-15 Copyright (c) 1994-2008 H. Peter Anvin".

Two question in short:
1. How can get the GRUB boot manager working again so that I can access my existing Vista and Ubuntu accounts?
2. How can I install XP without causing a problem like this again (my guess is that it partially installed the windows boot manager, then the whole thing failed)?[/COLOR]

---

### Post by kulturloseramerikaner on 2009-05-24
First things first - let's get you booting again.  I could be wrong, and I hope someone will correct me if I am, but if Windoze had succeeded in installing it's own bootloader you'd never have the GRUB error pop up in the first place.  GRUB error 17 means that GRUB can't reconcile the partition table it sees with the one it has stored.  When you tried installing Windoze XP you had to create another partition, and now GRUB's not sure where to look for the boot record.  Do you have access to another system you could use to download?  If so, download and burn an iso of this:

[http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.5-2.iso&a=99251298](http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.5-2.iso&a=99251298)

This nifty tool is essentially the partition editor Ubuntu uses, on a liveCD by itself.  Make sure you're set to boot from the CD drive on the system you're trying to restore, and start up with this in the drive.  After it loads, it'll give you the option of deleting and resizing partitions.  Since the XP install didn't work and you'll have to reinstall anyway, it'd be easiest to delete it first.  You can then use GParted to expand the partitions back out to cover the entire disk.  
BE VERY CAREFUL WITH THIS TOOL THOUGH! You can easily mess up the entire disk.  Basically, make certain the partition you are deleting is the one XP tried to create.
Once this is done, GRUB should only see the original 2 partitions and should start like normal.
If this solves the problem, you can go back in with GParted and shrink the existing partitions to make room for a clean XP install; you can even format the new partition in NTFS so that the XP installer can run on just a "quick format."

---

### Post by raymondh on 2009-05-24
Hello Apocalex13,

You can also use the liveCD to restore GRUB.  See this link (particularly the quick start)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This is also a link about GRUB for your reference

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Best of luck on either option/alternatives presented to you.

Regards,

---

### Post by raymondh on 2009-05-24
> **apocalex13 said:**
> [COLOR=#333333]
3. Attempted to install windows XP as well, but the installation process gave me a Blue Screen, so I stopped trying


Yes, that may have been it.

---

