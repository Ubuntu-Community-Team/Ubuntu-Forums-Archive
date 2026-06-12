---
title: "ubuntu on dell 9100 desktop - ubuntu breezy badger"
date: 2005-11-01
forum: Desktop Environments
---

### Post by mwolfe on 2005-11-01
Alright i've managed to get most things working on my new dell 9100, but i'm still having a few problems.  For 1, i dont really understand how the SATA stuff works. My current situation is this:
the computer came with 1 hard drive and 2 cd/dvd roms.  I had another hard drive though from my old computer with 160gb that i wanted to put in this machine, unfortunately it was IDE and this machine didnt have any extra IDE ports, so i went and bought a cheap little ide raid controller that has 2 ide ports.. I had some trouble getting it to work even with windows. I had to change some settings in my bios where i put it in combination mode. I couldnt get the new card/drive to work in any other setting.
Alright so then when i finally got everything working good in windows, I installed ubuntu.. the funny thing is that ubuntu didnt even recognize my SATA hard drive at all, it only recognized the hard drive connected to the ide raid controller.  luckily i had a free partition on that drive so i just installed ubuntu there.

Now, however i cannot see my other drive at all.. 
Also,  i cannot boot windows unless i change the boot priority to the sata drive on top of the ide drive (from my bios). I have to switch that around everytime if i want to boot windows instead of linux.. and then i have to switch it back to boot linux.. (not exactly convenient)..

Any ideas on how i might resolve some or all of these issues.
thanx in advance

---

### Post by mwolfe on 2005-11-02
any ideas on how to get ubuntu to recognize SATA at all?

---

### Post by RAOF on 2005-11-02
The sata drives will be handled as scsi drives, for reasons which escape me.  As such, they'll be found under /dev/sda*, /dev/sdb*, whatever, rather than /dev/hda, hdb, etc.  I didn't have to do anything to get ubuntu to notice my sata drives - what motherboard is in there?  It's possible that there is an obscure/new sata controller on it, which doesn't have linux drivers...

But first, I assume that you've checked that /dev/sda etc. aren't there, and they don't correspond to your sata drive(s)?

---

### Post by mwolfe on 2005-11-02
I believe it is the 945P chipset.. cpu is 8200. I do not have any listings for sda* in /dev/

i do have the /dev/sda though, but not entries for sda..

---

### Post by RAOF on 2005-11-02
I don't suppose that "sudo fdisk -l /dev/sda" gives any output?

---

### Post by mwolfe on 2005-11-02
nope.. here is the output though for fdisk -l
 

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4169    31517608+   7  HPFS/NTFS
/dev/hda2            4170       21175   128565329    f  W95 Ext'd (LBA)
/dev/hda5            4170        8926    35962888+  83  Linux
/dev/hda6            8927       20765    89502808+   7  HPFS/NTFS
/dev/hda7           20766       21175     3099568+  82  Linux swap / Solaris


i've been doing some more research, and it seems like its probably has to do with the way its configured.. there is an option in my bios as to how i want the system to handle the disk drives.. there are 4 different options, i tried setting up my system in all 4 configurations and the only one that worked with the ide raid controller card was the combination mode.. and for some reason i believe thats why linux isnt seeing it..

---

### Post by RAOF on 2005-11-02
That could be it, I suppose.  But the linux kernel is usually to wily to be put off by the bios.  But changing that bios option may help - give it a whirl.

---

### Post by mwolfe on 2005-11-03
Alright i got it working. I went in my bios and tried changing the option to RAID only.. 
unfortunately that didnt work by itself, i had to reinstall ubuntu.. I didnt know if it would work or not at first so i just went through with the ubuntu installer until it got to the disk formatter so i could check if all my drivers were present.. And they were, so i figured it would be easier to just reinstall now..

Everything looks like its working correctly now  though, and the installer recognized my windows partition so i no longer have to change the boot priority to boot into windows. 

One question though, all my drives are mounted automatically, unfortunately the ones that are ntfs I cannot read from unless i access it as root.. the other drives i can read from just fine.. 

here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc6       /media/hdc6     ntfs    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda4       /media/sda4     vfat    defaults        0       0
/dev/sda5       /media/sda5     ntfs    defaults        0       0
/dev/sda6       /media/sda6     vfat    defaults        0       0
/dev/sda7       /media/sda7     vfat    defaults        0       0
/dev/sda8       /media/sda8     vfat    defaults        0       0
/dev/hdc7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0
~
~
i've tried chown and chmod as root on the drives so i can make myself the owner but it won't let me since they are read only..

---

