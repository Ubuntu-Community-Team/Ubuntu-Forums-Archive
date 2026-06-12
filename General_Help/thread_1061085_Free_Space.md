---
title: "Free Space"
date: 2009-02-05
forum: General Help
---

### Post by jtcarstens on 2009-02-05
So I recently put Ubuntu 8.10 on a laptop on a seperate partition from windows xp pro. The partitions were seperated 60 gigs each, but when I'm in ubuntu it only says I have 9.6gb of free space. I can go into windows and look at the ubuntu partition, and it says i have 43gb free space. How do I get ubuntu to see the rest of the hard disk space on that partition?

---

### Post by Elfy on 2009-02-05
Can you run a couplle of things from a terminal (in applications > accessories) and the password you'll be asked for is your normal one and will be invisible

```
sudo fdisk -l
df -h
```

---

### Post by jtcarstens on 2009-02-05
Well I just got out of school and tried to boot to ubuntu to enter those commands, and i got to a blue screen that said there was an internal error, and X couldn't be located. SO I think I'm going to blow away the partition and start over. I'll keep you updated on how everything with the hard disk space goes.

---

### Post by jtcarstens on 2009-02-05
this is what came up when I typed sudo fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa43ca43c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       14593    55777680    7  HPFS/NTFS

df -h:
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.3G  2.2G  5.7G  28% /
tmpfs                 471M     0  471M   0% /lib/init/rw
varrun                471M  108K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M  2.8M  468M   1% /dev
tmpfs                 471M  240K  470M   1% /dev/shm
/dev/sda2              54G   11G   44G  19% /host
lrm                   471M  2.0M  469M   1% /lib/modules/2.6.27-7-generic/volatile

---

### Post by jerome1232 on 2009-02-05
It looks like it's still using the virtual disk. What was the method you used to migrate it to a real partition?

---

### Post by jtcarstens on 2009-02-05
I just installed inside of windows because I figured it would be the easiest. Any ideas?

---

### Post by jtcarstens on 2009-02-05
help me please!! I reinstalled and now I only have 5 gigs free. How do I get it out of virtual mode or whatever?

---

### Post by jerome1232 on 2009-02-05
> **jtcarstens said:**
> help me please!! I reinstalled and now I only have 5 gigs free. How do I get it out of virtual mode or whatever?

Instead of doing a Wubi install (installing inside windows), boot up of the cd and run the installer.

There's a very nice guide here.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jtcarstens on 2009-02-05
alright well when i boot to the 8.10 cd (which i know is 100% good because i just burned a new copy) it goes to like infrasim command prompt and just says type help for a list of commands?

---

### Post by Elfy on 2009-02-06
ASsuming that you checked the md5sum and have checked the integrity of the cd with the option on the boot menu then can you tell us how much RAM you have and graphics card.

You can if you want migrate to a real partition - [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I migrate to a real partition, and/or get rid of Windows entirely?

---

