---
title: "Want to install Windows 7 RC onto my Ubuntu rig..but how?"
date: 2009-05-06
forum: General Help
---

### Post by joseywales on 2009-05-06
Hello all.  I have a computer set up as a test rig, essentially I use it to play around with the various linux distros as a hobby.  Right now I have Ubuntu installed on the lone HDD, a 36GB raptor, and there are no other hard drives currently in the box.

I want to install the latest Windows 7 release client on the system to see what I think about it, however apparently the file systems are different to the point that when I insert the Windows 7 install disc there's a point during which the system cannot see the hard drive.  After a bit of research online it's apparent that I need to somehow get rid of Ubuntu and format the drive in such a way that it's compatible with the Windows format.

To a linux newbie, can someone please help me out...please?!?!

TYIA.

---

### Post by frodon on 2009-05-07
Moved to general help

---

### Post by freonchill on 2009-05-07
choices
1. install windows 7 after repartitioning the drive with freespace that windows 7 installer can use*
2. install windows 7 in virtual machine (vmware, virtualbox, xen)

*you might f-up grub (boot loader) so have a liveCD handy to fix it after windows install

---

### Post by joseywales on 2009-05-11
> **freonchill said:**
> choices
1. install windows 7 after repartitioning the drive with freespace that windows 7 installer can use*
2. install windows 7 in virtual machine (vmware, virtualbox, xen)

*you might f-up grub (boot loader) so have a liveCD handy to fix it after windows install

I apologize for not knowing exactly what it is you're recommending but I haven't been able to achieve my goal yet based on my research.  My question is, how to I clear the lone hard drive on my (trial, just for fun) computer that currently has Ubuntu installed so that it can accept an install of the latest Windows 7 Release Client?  For the purposes of this experiment I'm looking to blow away Ubuntu (short lived, just for curiosity's sake to play with the latest version of Windows) but because the file structure is so different I cannot install onto a HDD that isn't NTFS.

My question is how can I clear my existing HDD so that it is as if I had just opened the OEM box and installed it into any old regular box, regardless of what OS I had in store for it?

---

### Post by traderpats on 2009-05-11
I would say if you just wanted to blow away the existing partitions then use the WD tools cd.  If you don't still have it then I imagine you can download the utility.  I've never had that fail.  It'll load dos at boot and away you go...

---

### Post by max_power on 2009-05-11
hey man you can run windows 7 in a virtual machine

In ubuntu go to Applications -> accessories ->terminal

then type:

```
sudo apt-get install virtualbox
```

after you have installed virtualbox, fire it up and then it should walk you through setting up a virtual machine and running win 7

---

### Post by mike555 on 2009-05-12
if you want to use the whole harddrive to install 7 , you might need to clear the mbr .... then format it ntfs with gparted -- using a live ubuntu cd --

   to clear the MBR?


  In Linux , in terminal type;

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1



That will erase any MBR. If your drive is not /dev/hda then please use
the proper one (such as /dev/hde or /dev/sda or what have you)

---

### Post by Greenwidth on 2009-05-12
Just boot to the Win DVD at startup, select custom install (which you will have to if you don't have an appropriate partition) and follow the instructions. Windows will happily sort itself out / overwrite the universe, for you.

---

