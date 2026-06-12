---
title: "[very urgent] (initramfs) after a fresh install 8.10"
date: 2009-04-03
forum: General Help
---

### Post by reza81 on 2009-04-03
Hi ppl,

I installed ubuntu 8.10 on a HP xw4400 workstation because it has a sata controller bilt in and I need to make use of a 1.5TB HD for a NFS. (no raid needed)

After a fresh install i get the following:
```

Starting up...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat/proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (dis the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/ddf1_SimpleVol1 does not exist. Dropper to a shell!

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

```

I realy need to make this work, because bier is waiting in my fridge for me :D ... and it has to work for a desaster recovery test ... blabla 

tnx in advance

---

### Post by reza81 on 2009-04-03
BTW,

ddf1_SimpleVol1 >>> I made this volume at installation with a swap partition 3.1GB and / 150TB

---

### Post by sdennie on 2009-04-03
If beer is involved, that gets your thread a higher priority.  Fortunately, I think I know the answer.  You've created the root partition as LVM and the modules needed to use it to boot aren't in the initrd.  Unfortunately, I don't know how to fix that.  When I ran a file server, I ran the root partition as RAID1 and the home directory as RAID5 + LVM.  That way the system can boot from any of the disks and later brings the RAID5 + LVM array online regardless of which disk it actually boot from.

---

### Post by reza81 on 2009-04-03
I guess this means another fresh install... It's the 4th one today :S I am getting a bit crazsy... and need weekend ASAP! 

I had also installed it with RAID support btw had the samething.

Have not istalled anything as LVM tho, dont know what it is or do... 


Well, here goed the 5th install of today

---

### Post by reza81 on 2009-04-03
Did some reading

Oke now i initiated SATA RAID + LVM

see how that goes!

---

### Post by reza81 on 2009-04-03
Now I am getting:

```

GRUB loading, please wait...
Error 17

```

---

