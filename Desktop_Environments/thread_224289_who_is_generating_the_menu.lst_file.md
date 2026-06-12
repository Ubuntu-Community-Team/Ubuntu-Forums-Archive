---
title: "who is generating the menu.lst file?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by IdoMcFly on 2006-07-27
Hello,

I had a problem with grub on install and bumped into error 15.

After a couple of hours, I found that if I put hd0 instead of hd1 it can boot. But my main disc is hd1.

now each time the kernel is updated, the menu.lst is generated again and it put hd1 again and I have to edit the file myself to put hd0.

Where is define these hd1 and hd0 stuff? I've already switched the value in device.map but no success :confused:

---

### Post by jpkotta on 2006-07-27
The configuration is in menu.lst itself.  See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto).  If it doesn't make sense, post back here; I am the one who's trying to improve the update-grub stuff.

---

### Post by Jhongy on 2006-07-27
Look for a commented line in the "automagic debian kernels list" that sets what it thinks is the drive where GRUB is loaded from.

---

### Post by az on 2006-07-27
> **IdoMcFly said:**
> Hello,

I had a problem with grub on install and bumped into error 15.

After a couple of hours, I found that if I put hd0 instead of hd1 it can boot. But my main disc is hd1.

now each time the kernel is updated, the menu.lst is generated again and it put hd1 again and I have to edit the file myself to put hd0.

Where is define these hd1 and hd0 stuff? I've already switched the value in device.map but no success :confused:

Edit the 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

stanza in /boot/grub/menu.list accordingly.  Yes it is commented out, but update-grub parses the file for the defaults.

---

### Post by IdoMcFly on 2006-07-28
thank you all!

I did'nt kown that update-grub parses the commented stuff :)

---

### Post by pbardet on 2008-02-05
Please excuse my stupid question if it is, but I can't seem to find the answer anywhere in the documentation provided above.

I recently moved my /boot directory from a separate partition to my main partition.
Since then, everytime the kernel is updated, my menu.lst gets changed, but I can't seem to get the /boot added at the front of the initrd/kernel lines.

I was able to get the proper drive used (hd0,2) thanks to the explanation above, but the /boot is still missing. I compared my menu.lst to a fresh install of mythubuntu (uses only one partition for everything) but I can't seem to find where the /boot comes from. Is it from an external file ?

Thanks in advance.

---

