---
title: "how to delete the previously installed ubuntu 32bit?"
date: 2009-04-04
forum: General Help
---

### Post by coconut73 on 2009-04-04
I had ubuntu 8.10 32 bit installed, and today I just installed ubuntu 8.10 on the same machine, same HDD. 

Now in the boot menu, it has 2 ubuntu systems, and when get into the newly installed ubuntu, the old ubuntu 32bit seems still in the drive sda5. I just want to wipe out the old 32 bit ubuntu. Is there any way to delete it?

During the new installation, I did not do much tweak in the partition, just did partition resizing, did not delete sda5, where the old ubuntu 32 bit sitting. 

I do want to clean it up, thanks for your help.

---

### Post by Elfy on 2009-04-04
I would have just installed over the top of it.

Boot the livecd - in the System Admin is a partition editor - you can delete/reformat or delete and then resize your new install to use the space.

---

### Post by coconut73 on 2009-04-05
I have the old 32bit ubuntu installed on /dev/sda5, and new 64bit ubuntu on /dev/sda7.

When boot up use live cd and try to delete /dev/sda5, the partition editor said : unable to delete /dev/sda5, please unmount partitions with number higher than sda5. 

But the unmount option of /dev/hda7 in peditor is greyed out.

So, what should I do next ?

Thanks!

---

### Post by zvacet on 2009-04-05
Try with [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by -kg- on 2009-04-05
What is sda6 used for?  Swap?  You might try that.

I can't understand why the partitions would be mounted when booting from a LiveCD, anyway.  It doesn't make any sense to me.

You might try downloading the [GPartEd Live CD]("http://gparted.sourceforge.net/") and do your partitioning operations from there.  I've never had the issue of partitions being mounted using it.  You should be able to delete sda5 using that.

One caveat, though...you're probably going to have to do some editing of GRUB's menu.lst after you're done.  The partition's identifiers are going to change (i.e., sda7 will become sda6 and sda6 will become sda5) and you're likely to have booting problems.

Not a problem though.  You can even reinstall GRUB, correcting the problems.  Just go to the following link and follow the directions given in the third post down:

[http://ubuntuforums.org/showthread.php?t=1114171]("http://ubuntuforums.org/showthread.php?t=1114171")

---

### Post by coconut73 on 2009-04-10
Yes, the GPeditor Live cd works pretty good, I deleted the ext3 partition and made it ntfs. That is wicked cool.
Thanks.

---

