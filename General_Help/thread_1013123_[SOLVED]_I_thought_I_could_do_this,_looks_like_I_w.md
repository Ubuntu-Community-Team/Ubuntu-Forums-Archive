---
title: "[SOLVED] I thought I could do this, looks like I was wrong (windows dual boot)"
date: 2008-12-16
forum: General Help
---

### Post by Gonz_91 on 2008-12-16
Hi everyone!

So, today my project was to install Windoze XP alongside my dear Ubuntu 8.10 install.
Easy, I thought. So, I pop the cd in, choose the unpartitioned space, etc etc... Until I'm on a fresh XP desktop.
So, I then reboot, boot Ubuntu via USB and ran
```
sudo grub-install /dev/sda
```
So that GRUB would work again, and that menu.lst would list both Ubuntu and Windows.

But, instead of the normal output, I get:
> Could not find device for /boot: Not found or not a block device.

What is the meaning of this?
Any ideas on how to get the thing working?


Thanks in advance

---

### Post by lykwydchykyn on 2008-12-16
Are you sure the disk is actually /dev/sda when booted to USB?

I would try this:
```

sudo grub
root (hd0,0)
setup (hd0)

```

See if that works.

---

### Post by logos34 on 2008-12-16
post the output of 

sudo fdisk -l

You have to manually add windows entry to grub [this way]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu")

---

### Post by Gonz_91 on 2008-12-16
> **lykwydchykyn said:**
> Are you sure the disk is actually /dev/sda when booted to USB?

I would try this:
```

sudo grub
root (hd0,0)
setup (hd0)

```

See if that works.

Well, that got me booting back into ubuntu.


> You have to manually add windows entry to grub this way

That got me nowhere, yet. I edited menu.lst as suggested, but when I choose that option, it boots into ubuntu.


fdisk -l gives back the following output:
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc98bb51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2741    22017051   83  Linux
/dev/sda2            3264       21580   147131302+  83  Linux
/dev/sda3           21581       24320    22009050    7  HPFS/NTFS


(yes, I am aware that I am not currently using any swap partition)

---

### Post by doobiest on 2008-12-16
windows should be in menu.lst as hd0,2 as it's the first drive, 3rd partition

title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by doobiest on 2008-12-16
Also if you're unsure, you can always highlight windows xp from the grub boot menu and hit 'e' to edit. and you can mess around with the boot params until you get it right. Then once you have it right, make it permanent in the menu.lst

---

### Post by Gonz_91 on 2008-12-16
> **doobiest said:**
> windows should be in menu.lst as hd0,2 as it's the first drive, 3rd partition

title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

That was it. I tought of it and changed immedeately, so now I'm posting from Windows.


Thank you all very very much for your help!

I hope that in the near future, the already fantastic Linux can substitute windows, so that all this is unnecessary :D


*marking as solved*


(ps: looks like I was right after all, xD)

---

### Post by doobiest on 2008-12-16
Get rid of windows. Just install virtualbox and get a copy of crossover games to install all your windows games. ;-)

---

### Post by Gonz_91 on 2008-12-16
> **doobiest said:**
> Get rid of windows. Just install virtualbox and get a copy of crossover games to install all your windows games. ;-)

I thought of that, but I also have a few applications that need to be run in Windoze, like EarMaster and Office 2007.


I do know that these applications can be run in Ubuntu, but barely, and it's quite a challenge to get them working. For now, this is the best solution.

---

### Post by doobiest on 2008-12-16
Virtual box is a VM of windows so it's a full windows desktop overlayed on your ubuntu desktop. You can run everything except directx (3d) apps.

So that will run office.  Even if you dont want to run a full windows instance and would rather just emulate individual applications use wine.  For the record I run ms office on my work laptop using wine, works good. I also run all my games through wine and they behave very well.

I highly recommend an app called crossover, which is a front end to wine that does all the config for you.  It used to be free, im not sure anymore

---

