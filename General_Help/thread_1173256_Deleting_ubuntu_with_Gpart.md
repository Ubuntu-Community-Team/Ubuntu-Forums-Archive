---
title: "Deleting ubuntu with Gpart"
date: 2009-05-29
forum: General Help
---

### Post by SGer on 2009-05-29
Hi, I've installed unbuntu and while allocating it space alongside winows through Gpart, My computer collapsed, thus deleting everything on my hardrive.
I installed windows, and now I was about to install ubuntu from the disk, but unfortunatlly I discovered that I can't install it on the space that already allocated to the "old" ubuntu.
So, I entered the Ubuntu demo from the disk. lunched Gpart, and I've found that a key symbol is apearing next to the space that is allocated to Ubuntu (named as /dev/sda3) . which means. I can't delete it.
My friend told my i have to command " umount /dev/sda3 " on Terminal.
I've tried this, but it keeps telling me something like "dev/sda3 is not mounted, according to Mtab"
 
what can I do? how can I delete this space so I can install "new" ubuntu on this space?
Thank you!

---

### Post by Therion on 2009-05-29
Boot from a gParted LiveCD and reformat the drive.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by SGer on 2009-05-29
But I wouldn't like to delete the partition that is allocated to windows.
Is reformatting the hardisc won't delete EVERYTHING I have on the disc? including windows?

---

### Post by Therion on 2009-05-29
> **SGer said:**
> But I wouldn't like to delete the partition that is allocated to windows.
Is reformatting the hardisc won't delete EVERYTHING I have on the disc? including windows?
Ah, okay... Well the gParted LiveCD will allow you to modify your partitions as well.  The problem you're running into, if I read your OP correctly, is that even when using the Ubuntu LiveCD (to access the Partition Editor) the hard drive you want to play with is being mounted.  You can't modify partitions on a mounted volume.  The gParted LiveCD will not mount the drive and allow you to do whatever it is you want/need to do to your drive and its partitions.

So, in short, the answer is the same.  Burn a bootable gParted LiveCD and go nuts.

---

### Post by SGer on 2009-05-30
Thanks a lot!
It worked perfectly smooth! without any errors this time.
So now I have My ubuntu installed alongside windows .
thank you,
  Sagy.

---

### Post by Therion on 2009-05-30
Excellent, glad that worked out for you.

---

