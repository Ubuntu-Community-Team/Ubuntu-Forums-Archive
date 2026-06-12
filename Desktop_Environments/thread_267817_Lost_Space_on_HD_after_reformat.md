---
title: "Lost Space on HD after reformat"
date: 2006-09-29
forum: Desktop Environments
---

### Post by FunWithSoil on 2006-09-29
Hello everyone, 
First I just started experimenting with ubuntu a few months ago and love it so far.  

My problem is, I had a dual boot XP, then ubuntu going.  After disk errors occasionally in windows, realized by running chkdsk in xp and at boot up with ubuntu i decided to reformat.  And this was a brand new drive that had no problems for a while until i started playing with ubuntu, not that ubuntu has to have caused it.  Anyways i had an elaborate partitioning scheme for windows. Windows used 3 primary partitions and 2 logical on the extended partition.  I installed ubuntu on some logical drives on the same extended partition that already contained windows stuff (i know i was pushing it).  

So after reading this:
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
" WARNING: The used partitioner, GParted, is old, very buggy and can corrupt the partition table!" about ubuntu 6.06, i decided to start over (windows was getting slow and i wanted a clean install of edgy anyways).  By the way if that last statement is true something should be done.

So I actually put the drive in an external enclosure(this is a laptop im talking about) and booted from an older drive with xp and i deleted all partitions on this drive in question using disk management in xp.  Then put the "clean" drive back in the notebook, pop in xp install cd. It sees 74gb, cool its an 80gb drive.  So i create a 15 gb partition and format for xp. I go through the install process and 2 hours of getting drivers and everything the way its supposed to be only to find out in disk management that its not seeing the whole drive.  It only sees 55gb, basically can't see the space that ububtu was using.
So now i put in the xp install disk to reformat and it doesn't even see the full size there. now only 55bg!

Of course I'm extremely frustrated.  

Look at all the posts from people with similar situations 
nothing worked....
This one gave me hope, so similar.....yet nothing.
[http://www.ubuntuforums.org/showthread.php?t=109074&highlight=lost+space+reformat](http://www.ubuntuforums.org/showthread.php?t=109074&highlight=lost+space+reformat)

A friend said he had the same prob when trying ubuntu then reformatting, reformatted multiple times and cant remember how it was fixed! great...

Someone told me about the ultimat boot cd, used Darik's Boot and Nuke. Ran hitachi diagnostics ...sees only 55gb.

so.. any suggestions

So desparatly trying to make the switch, but might not reinstall ubuntu if the partitioner really messes stuff up like that site says.

---

### Post by FunWithSoil on 2006-09-29
oh man, i just realized. I cant remember if i had that thing installed on my windows laptop that lets you see ext2,3 partition. In the case i didn't then when i deleted the partitions from windows while the drive was in an external enclosure, all the ubuntu stuff wasn't deleted.  Hmm, now that I think of it there was a grub error when booting with the drive in the external enclosure because external usb device was before internal hd in the bios boot sequence. Forgot to mention all this, its late.  Anyways, once I did that first reformat the grub errors went away.  Well i'll try intalling windows, then installing that thing that lets me see ext2/3 partitions then try and delete them if they show up.... That may be it. I'll get to it tomorow night, let me know what you think.

---

### Post by FunWithSoil on 2006-09-30
So, after using Ext2 IFS for Windows wich lets me see ext3 formatted partitions which my ubuntu partitions were formatted in, I could not see them.  Any suggestions?

Thanks in advance for any help.

---

### Post by FunWithSoil on 2006-10-01
Well I'm still trying. I reinstalled linux and tried using parted to resize my the last partition into the lost space, but it tells me

Error: The location 70GB is outside of the device /dev/sda. Again it is an 80gb drive so i know i can extend out to 70gb.

I really appreciate any help.  Is there other info that I am leaving out that  is needed? 

Thanks in advance.

---

### Post by FunWithSoil on 2006-10-01
I ended up installing fc5 and seeing if that installer could fix it.  It didn't.  Here is the output from fdisk -l
```
[root@localhost ~]# fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        7113    57030750   8e  Linux LVM

Disk /dev/dm-0: 56.2 GB, 56270782464 bytes
255 heads, 63 sectors/track, 6841 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-1 doesn't contain a valid partition table


```

---

