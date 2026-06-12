---
title: "Uninstall Ubuntu"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Jordan Meeter on 2006-01-28
Hello,

After months of being unhappy with Ubuntu, I've decided to uninstall Ubuntu and go back to Windows XP.

My question is, what is the safest way to "uninstall" Ubuntu, and and get rid of the GRUB/dual boot menu?

Thank you.

---

### Post by earobinson on 2006-01-28
just install xp over it and it will all be gone

---

### Post by Jordan Meeter on 2006-01-28
I already have Windows XP on the computer...

---

### Post by Herman on 2006-01-28
Well, you can try [this link, ]("http://users.bigpond.net.au/hermanzone/p18.htm")it should tell you all you need to know.
 I also think [GParted on its own live CD]("http://gparted.sourceforge.net/livecd.php") is the best partitioning software you can get. You could use that to delete the Ubuntu partitions and resize your Windows partition. (Herman).

---

### Post by Jordan Meeter on 2006-01-28
I opened msconfig, went to the BOOT.INI tab and didn't see anything about GRUB - Can I just delete the Ubuntu partition? I don't want to get the GRUB error 17 thing.

Oh, btw. I can't do the /fdisk mbr thing because i don't have a floppy drive. =\

---

### Post by Herman on 2006-01-28
Well, if you have Windows xp, and still have / or can borrow the installation disks for that, you should be able to do [this.]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp") 
Other then that, another solution would be to use GAG bootloader, it's already on system rescue CD, you can install that to MBR, overwriting GRUB, and it will boot Windows for you just fine! You can also make your own GAG CD if you want, read all about GAG [here]("http://users.bigpond.net.au/hermanzone/p12.htm").
Yet another idea is to copy the boot disk floppy files to a CD. they will still work the same I'm pretty sure, just that it's a waste of a good CD to only use it for such a small number of MBs. I forget whether I ever tried that or not, but when you view the files on the floppy disk, and view the files on a Microsoft CD, they are just the same files as far as I can see.

---

### Post by olddog55 on 2006-01-28
If you don't want to go through the hassle of resizing partitions: Use the procedures cited in the "Using the Recovery Console to Replace the MBR" [from above]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp").  If you don't do any repartitioning, you'll wind up with the (known) Windowz partition and an 'unknown' second partition which contains the old Linux stuff.  At your convienience you can reformat and assign it as a second windowz partition.  The procedure installs a brand new boot sector, overwriting the grub info but leaving the disk partition information intact.

---

