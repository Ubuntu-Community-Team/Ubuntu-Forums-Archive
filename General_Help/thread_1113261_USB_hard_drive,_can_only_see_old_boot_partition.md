---
title: "USB hard drive, can only see old boot partition"
date: 2009-04-01
forum: General Help
---

### Post by mattotoole on 2009-04-01
I've connected my old hard drive to my new laptop vis USB, to transfer the data to the new machine.  The drive spins up and seems to mount fine, but all I can see is the boot partition (the drive appears on my desktop as _boot)

How do I see and mount the other partitions so I can get my data?  I think I just have one big partition besides swap and boot.

AFAIK the drive is fine.

I'm running a brand new Hardy with all the updates.

---

### Post by mattotoole on 2009-04-03
Bump.  Anyone?

---

### Post by coffeecat on 2009-04-03
If it's only automounting the one partition, it may be that the partition table or the partitions themselves are corrupted.

To check this out, post the output of this terminal command:

```
sudo fdisk -l
```If you want to check it out graphically, install gparted via synaptic. Once installed you can find this at System > Administration > Partition Editor. Plug in the USB drive and then open Gparted. Go to the little drop down box at top right and select your USB drive (probably sdb if you have no other devices attached).

---

### Post by mattotoole on 2009-04-03
I can see the partitions with fdisk:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32        4870    38869267+   5  Extended
/dev/sdb5              32        4870    38869236   8e  Linux LVM
```

I haven't tried it yet but I assume I can access my files with the command line.  I don't know how from here.

Ultimately, how would I fix my system so I can do it with the File Manager?

---

### Post by coffeecat on 2009-04-03
sdb1 must be your /boot partition, but sdb5 is a LVM partition. Maybe that's why it won't mount. Sorry, but I have little experience of LVMs. When I tried to understand how they worked, I got a severe headache and had to lie down. :( :wink:

Sorry I can't help further, but at least fdisk has given a clue. Try a search for mounting LVM volumes/partitions. You might come across something.

**Edit:** [This might help]("http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html").

You'll need to preface all those terminal commands with sudo, of course.

---

### Post by mattotoole on 2009-04-03
coffeecat -- thanks!  I'm confident that's where the answer is.  

About the LVM -- I know what it is (a virtual partition that can be spread over several physical drives), but I have no idea how to use it either.  I never intended to have it, it just installed itself when I installed Ubuntu 5.10 on this drive.

Anyway I'll keep looking into the LVM thing.  Maybe someone else could give me a hint or two.

---

### Post by CyberMando on 2009-04-03
sudo aptitude install lvm2
after that it will recognize your Logical volumes. They will probably be listed in /dev/mapper.

---

### Post by mattotoole on 2009-04-03
> **CyberMando said:**
> sudo aptitude install lvm2
after that it will recognize your Logical volumes. They will probably be listed in /dev/mapper.

Done.

Now I can see the volumes but I don't know how to mount them.  The drive is still showing up on my desktop as /boot.  Here's my terminal output.  It's been years since I dealt with mtab or fstab.  ???

```
matt@matt-laptop:/dev/mapper$ ls
control  Ubuntu-root  Ubuntu-swap_1
matt@matt-laptop:/dev/mapper$ mount Ubuntu-root
mount: can't find Ubuntu-root in /etc/fstab or /etc/mtab
```

---

### Post by CyberMando on 2009-04-03
You could add a line like this to /etc/fstab if you want it mounted at boot time
/dev/mapper/Ubuntu-root        /Ubuntu_root    ext3    defaults        0       2
The mount point, /Ubuntu_root, must exist. Then 
sudo mount /Ubuntu_root
will get it mounted.
For a one tiime mount
sudo mount -t ext3 /dev/mapper/Ubuntu-root /Ubuntu_root
.

---

### Post by mattotoole on 2009-04-03
CyberMando,

Got it.  It works.  Thanks!

---

### Post by gramoun_kal on 2009-11-16
Thanks! Saved my *** too.

---

