---
title: "Question about mirgate to ext4"
date: 2009-06-09
forum: General Help
---

### Post by carfield on 2009-06-09
According to [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4) . It is better to have /boot still in ext3, is that still valid suggestion?

For now I only have / partition, if I going to create another partition for /boot . Am I just create it and copy data from / partition to new partition? Anything else need to take care of?

---

### Post by sdennie on 2009-06-09
If you are using Jaunty, it can read /boot if it is ext4.  The version of grub in Jaunty has been patched for it but, you can also take the Ubuntu patch and apply it to the raw grub 0.97 source and it works fine.

---

### Post by carfield on 2009-06-10
Yes I am using Jaunty, great to know I don't need to create other partition just for boot. 

From that article it also mentioned using "tune2fs" and "e2fsck". Can I do that after mounting the disk?

---

### Post by alphacrucis2 on 2009-06-10
> **carfield said:**
> Yes I am using Jaunty, great to know I don't need to create other partition just for boot. 

From that article it also mentioned using "tune2fs" and "e2fsck". Can I do that after mounting the disk?

No. The partition can not be mounted when you do the conversion. I did mine by booting the Jaunty liveCD and running tune2fs from there. Make sure you let the e2fsk run to completion then don't forget to modify the /etc/fstab to match

---

### Post by Arup on 2009-06-10
The beauty of ext 4 is fast boot when Ubuntu root is installed in it. Also Ubuntu thankfully allows boot from ext 4 partition unlike the newly released Fedora 11 which still needs ext3. Another point to consider is that when you convert existing ext3 to ext4, the benefits only come with files written after the conversion, the older files remain in ext3 mode.

---

### Post by colau on 2009-06-10
ext4 is faster than ext3 during booting.

---

