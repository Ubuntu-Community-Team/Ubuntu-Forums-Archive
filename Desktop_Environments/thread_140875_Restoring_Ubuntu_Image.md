---
title: "Restoring Ubuntu Image"
date: 2006-03-07
forum: Desktop Environments
---

### Post by daz4126 on 2006-03-07
Hi,

I've been experimenting with dual booting for a while now and enjoyed using ubuntu.

My current HD set up is 

hda - windows
hdb 1st partition - linux, 2nd partition - home, 3rd partion - swap

I decided to give SUSE a try, so used norton ghost to make an image of the first linux partion and then installed SUSE onto that. I didn't like it as much as Ubuntu, so decided to put the Ubuntu partition back on, so I used ghost to make a copy of the SUSE partion and then restored the Ubuntu partition. When I rebooted, GRUB presented me with the usual Ubuntu options but then says it can't find any of the files - even Windows. If I restore the SUSE image, then everything works again, so I think there must be something else that I need to do besides just restoring the ubuntu image to get Ubuntu back, any ideas anybody??

thanks in advance,

DAZ

---

### Post by syg00 on 2006-03-07
I'm no fan of the imaging solutions - even less so the commercial products.

Re-install grub - all bootloaders are sensitive to the location of their files.

---

### Post by cotcot on 2006-03-07
I always copy the MBR (dd if=/dev/hda of=backup-hda.mbr count=1 bs=512) and the partition table (sfdisk -d /dev/hda > backup-hda.sf)  together with the image. For the image itself i use "partimage" from a live CD.

---

### Post by syg00 on 2006-03-08
Better hope those files aren't created on the same physical disk (i.e. /dev/hda).
Because when you *really* need them, guess what ....

---

### Post by daz4126 on 2006-03-09
Hi everybody,

Thanks for the help. I'm a bit too much of a newbie to understand everything here.

sysg00 - How would I reinstall Grub without doing a full install? and what do you mean about the files being on the same physical disk???

cotcot - It appears that I may have missed the boat on saving the mbr and partition table for ubuntu, so maybe a new install is on the cards. with regards to using partimage. I would prefer this as I'm trying to ween myself away from Windows and commercial products. Is it the ubuntu live disc you use and is there a decent guide to using partimage?

thanks for the help and sorry for not knowing too much - DAZ

---

### Post by syg00 on 2006-03-09
A quick search found [ this](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29) as the first hit.

My last comment was directed at cotcot, but think of it logically - no point in backing up the partition table of hda onto hda.
In the (unlikely) event the partition needs to be restored, you can't because to locate the file you require a valid partition table.

kaboom ...   ;)

---

