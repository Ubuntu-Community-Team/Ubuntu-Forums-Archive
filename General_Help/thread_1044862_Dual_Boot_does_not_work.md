---
title: "Dual Boot does not work"
date: 2009-01-19
forum: General Help
---

### Post by Redbox1 on 2009-01-19
I recently installed Ubuntu onto a machine currently running Windows XP. The system automatically boots to Ubuntu, instead of giving me a menu to choose from. I'm thinking I may have not partitioned the HD in the right way, but I'm not sure. (I'm new to Linux, so I probably messed it up somehow!)

Any ideas on why it could be doing this?

---

### Post by Ajtucker22 on 2009-01-19
I think I've done the same thing, and may have accidently deleted part of, if not all, of Vista on my new computer. I have no files worth saving, i just really want to logg back into vista.

---

### Post by saidan536 on 2009-01-19
I also Had issues with the new version of ubuntu. I believe it is a issue with settings during the setup. I have six hd's and only the first is ide the others are sata. One, My second hard drive is empty because I wanted to install linux to just that drive. However while the partitioning works and the files are installed I get just windows and the ubuntu dual boot screen does not come up at all

---

### Post by linux_nc on 2009-01-19
you have to manually partition your harddisk for dual boot, suppose you are running a pc of 80 gb harddisk in windows xp with 2 partition 40 gb each, now in manual partition during instalation, delete the d drive first(c having windows installed, don't touch it), click create a new partition> 2048 mb space> create another one with remaining space.that 2048 mb partition must be edited to swap space and remaining partiotion edited as "/", u're done.

---

### Post by 3DGE on 2009-01-19
Try going into your BIOS on main startup by pressing Delete or F8 then change your Boot settings to your other hardrive.

---

### Post by caljohnsmith on 2009-01-19
How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
That will give us some idea if you still have your Windows partition or not.

---

