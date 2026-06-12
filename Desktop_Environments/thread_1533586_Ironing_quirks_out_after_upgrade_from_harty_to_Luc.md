---
title: "Ironing quirks out after upgrade from harty to Lucid"
date: 2010-07-18
forum: Desktop Environments
---

### Post by wonderfullyrich on 2010-07-18
I've got a Dell d420 with 2gb of ram and a 80 gig drive in that's running Lucid.  I've been using Ubuntu on it for several years now and I started with Feisty on this laptop and have only upgrade using the LTS releases.  

First and foremost it works.  I love ubuntu, but I've got some serious annoyances that are driving me nuts.  I'm in Uganda with limited resources and internet that's bandwidth capped so I don't have all the tools I'd like to have.  

Here's a brief list of what's wrong in the order of priority:
*Firefox is not working.  executing it from the command line reports: 
```
rjeong@yunnus:~$ firefox %u
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

```
It looks as if Firefox isn't actually installed and I can't get it to install.
*Running Google chrome & Prism, after a long period (8+ hours) the hard drive spins and the computer becomes extremely slow at responding. So slow the mouse interrupt only intermittently responses.
I turned swap off, start closing things, and it works fine.  This didn't used to happen in Hardy, but I'm not yet an linux guru enough to tweak it to stop flipping out.
*mencoder is no longer working (the upgrade screwed something)
*Sound icon is not on the panel 
*Start up sound is now a scratchy bit of atmospheric noise and I can't tell it to shut up.
*update manager is firing off every day, even if I tell it not to.

Now admittedly, I should probably just backup my packages, move the data off, do a clean load, but I only have the one computer left due to some untimely netbook deaths and random backlight failures.  Besides that I need to learn how to use the more ample toolsets in ubuntu to tweak and clean up the OS.  (Been a windows boy for to long.)  I'm not looking for perfection, I just need it to basically work. 

Can anyone give me some guidance on one or more of the issues above?

---

### Post by lovinglinux on 2010-07-19
About Firefox, re-installing xulrunner should fix that error message. Go to Synaptic, search for xulrunner, mark the installed package for re-installation and apply. 

Anyway, since you are experiencing several issues, I would consider reinstalling Ubuntu. Since you can't make a backup, you could create a new partition, move your home to it and then reinstall, preserving the home partition. See [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by wonderfullyrich on 2010-07-21
Thanks lovinglinux.  The xulrunner is turning out to only be the beginning of it.  I ended up opting for [paid support]("http://shop.canonical.com/product_info.php?products_id=529").  $150 to canonical and I get the learning I'm after.  

Good idea on the partition though.  That might be a better option then clonezilla and wiping clean as I was considering. We'll see how the paid support works out.

Rich

---

### Post by lovinglinux on 2010-07-21
> **wonderfullyrich said:**
> Thanks lovinglinux.  The xulrunner is turning out to only be the beginning of it.  I ended up opting for [paid support]("http://shop.canonical.com/product_info.php?products_id=529").  $150 to canonical and I get the learning I'm after.  

Good idea on the partition though.  That might be a better option then clonezilla and wiping clean as I was considering. We'll see how the paid support works out.

Rich

You are welcome.

---

