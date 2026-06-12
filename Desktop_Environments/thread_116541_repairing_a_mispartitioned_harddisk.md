---
title: "repairing a mispartitioned harddisk"
date: 2006-01-12
forum: Desktop Environments
---

### Post by pataphysician on 2006-01-12
i installed ubuntu on a machine with a SATA drive and a PATA drive. the PATA drive had, i believe, two NTFS partitions: windows and data. during the install, ubuntu installed itself to the SATA drive (which is what i wanted), but i think for some reason wrote (or tried to write) GRUB to the PATA drive. after the install, nothing would boot. so i installed again, and that went fine.

my problem is that the partition table on the PATA drive is messed up and the drive is unreadable by either ubuntu or windows (i tried it in another machine). i don't care if the windows install is hosed, but i'd like to get my data back, if possible.

so, my question is, can i re-write/fix the partition table without further risking the data on the drive? and if so, what exactly would i do?

here is the sfdisk. hopefully this is enough for someone to walk me through fixing it. if you need more information, let me know. thanks!

```

root@sisyphus:/dev# sfdisk -l

Disk /dev/hda: 14593 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
llseek: Invalid argument

sfdisk: seek error on /dev/hda - cannot seek to 2181086913
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1     135766+   5456- 137040- 1100769085    f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (131,130,1)
/dev/hda2   * 137038+   6217- 136529- 1096663902+   6  FAT16
                start: (c,h,s) expected (1023,254,63) found (1023,130,1)
/dev/hda3     137805+  18774- 148319- 1191367652+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,130,1)
/dev/hda4     135765+   4181- 135766- 1090535680    0  Empty
                start: (c,h,s) expected (1023,254,63) found (130,130,0)
                end: (c,h,s) expected (1023,254,63) found (130,130,0)

```

---

### Post by pataphysician on 2006-01-13
bump? sorry, i don't know what to do here!

---

### Post by psusi on 2006-01-13
Wow, that is really clobbered up.  The first time you installed, did you do anything weird like tell the installer to set up lvm or raid?  Or did you tell it to format and install to /dev/hda or something?  ( Instead of /dev/hda1 )

I hope you have backups.

---

### Post by dabang on 2006-01-13
That doesn't look good... (Not what you wanted to here. ;) ) I made the experience that sometimes deleting a partition and then recreating it doesn't always mean the loss of the data (which I don't understand...) So maybe you could try this. But be warned: **there's no guarantee it works...**

---

### Post by psusi on 2006-01-13
Yes, if you know EXACTLY how the partitions were set up before, and you recreate them exactly the same way, there is a decent chance that the data itself is still intact.  

As for why, that's rather simple: editing the partition table only changes the listing in the MBR, it doesn't muck with the actual data.  

[QUOTE=dabang]That doesn't look good... (Not what you wanted to here. ;) ) I made the experience that sometimes deleting a partition and then recreating it doesn't always mean the loss of the data (which I don't understand...) So maybe you could try this. But be warned: **there's no guarantee it works...**[/QUOTE]

---

### Post by pataphysician on 2006-01-13
thanks for the replies. i don't know what went wrong during the install, i don't think i asked it to do anything out of the ordinary. i also don't know how the partition table was set up before. maybe i'll try a few desperate things wen i get home -- what do i have to lose, right? what's the safest way to go about recreating the partition table?

---

