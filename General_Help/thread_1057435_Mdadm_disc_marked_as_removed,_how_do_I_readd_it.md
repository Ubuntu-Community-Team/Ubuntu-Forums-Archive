---
title: "Mdadm disc marked as removed, how do I readd it?"
date: 2009-02-01
forum: General Help
---

### Post by Fredrik_b on 2009-02-01
```
ad@server:~$ sudo mdadm --detail /dev/md3
/dev/md3:
        Version : 00.90
  Creation Time : Wed Jul  9 22:50:11 2008
     Raid Level : raid5
     Array Size : 2197723392 (2095.91 GiB 2250.47 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Mon Feb  2 02:06:59 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e53386f5:388251a8:01f9e43d:ac30fbff (local to host server)
         Events : 0.845426

    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       0        0        1      removed
       2       8       80        2      active sync   /dev/sdf
       3       8       48        3      active sync   /dev/sdd

```

As you can se RaidDevice 1 is marked as removed for some reason. How do i re-add it?

I dont dare to try any more commands, but my next try would have been:

mdadm --verbose --assemble --force /dev/md3  /dev/sde /dev/sdc/ /dev/sdf /dev/sdd

---

### Post by Fredrik_b on 2009-02-02
Fdisk - l

> Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d5663e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           1         512    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdd3               1           1         512    0  Empty
Partition 3 does not end on cylinder boundary.

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d5663e9

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table


Update:

Now when I type: "sudo mdadm --detail /dev/md3" my computer frezes.

---

### Post by fjgaude on 2009-02-03
I'm not sure I can be of any help. Do you have md0/1/2 besides md3?

What does a **df -m** show?

---

### Post by Fredrik_b on 2009-02-03
I now Ran:
```
sudo mdadm --create --verbose /dev/md3 --level=5 --raid-devices=4 /dev/sde /dev/sdc /dev/sdf /dev/sdd
```

And it gave me this message

```
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sde appears to contain an ext2fs file system
    size=-2097243904K  mtime=Tue Feb  3 01:07:31 2009
mdadm: /dev/sde appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Feb  3 16:12:39 2009
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Feb  3 16:12:39 2009
mdadm: /dev/sdf appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Feb  3 16:12:39 2009
mdadm: /dev/sdd appears to contain an ext2fs file system
    size=-1828808448K  mtime=Tue Feb  3 08:37:33 2009
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Feb  3 16:12:39 2009
mdadm: size set to 732574464K

```

i pressed Y and it started to reassemble but slow 963k/s

And after 30 sec my computer stopped responding and required a hard reboot.

what can be wrong?

It also said that /dev/sdc hade no superblock when I ran another command (cant remeber the command right now)

The computer ran fine for 104 days with no problem before something went terribly wrong and I ended upp reinstalling the system, Now Ubuntu server 8.04, before xubuntu 8.04.

---

### Post by fjgaude on 2009-02-03
Well, it's hard to say what might has started it all... hardware likely.

When you use --create I do believe you destroy any data that might have been on the drives.

Do you have partitions on the four drives?

Also you can't create an array from drives that have been part of an older array without zero-superblock of each drive:

```
sudo mdadm -zero-superblock /dev/sdc
```

for each drive.

Do you have or had backups for important data.

You might find this link useful:

[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

Lots of things to learn when using software raid, what to do, what not to do, and when to do or not do.

---

### Post by Fredrik_b on 2009-02-03
I don't believe I ever had any partitions on those drives
at least not annt that I could se suing fdisk -l

/dev/sdd seem to have lost all knowledge of it ever being a part of a raid array so I assume the data on that one is gone. But nothing is lost if I can mange to rebuild the array with the remaining 3 drives.

/dev/sdc seam to have fixed itself.

/dev/sdf is the trouble now

When I run:

sudo mdadm --create --verbose /dev/md4 --level=5 --raid-devices=4 /dev/sdd /dev/sdc /dev/sdf /dev/sdf

I get 


> mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdd appears to contain an ext2fs file system
    size=732574584K  mtime=Thu Jan  1 01:00:00 1970
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=4 ctime=Wed Feb  4 00:41:51 2009
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=4 ctime=Wed Feb  4 00:41:51 2009
mdadm: /dev/sdf appears to be part of a raid array:
    level=raid5 devices=4 ctime=Wed Feb  4 00:41:51 2009
mdadm: /dev/sdf appears to be part of a raid array:
    level=raid5 devices=4 ctime=Wed Feb  4 00:41:51 2009
mdadm: size set to 732574464K
Continue creating array? y
mdadm: failed to open /dev/sdf after earlier success - aborting


/dev/sdd is weard whatever I do, mdadm always thinks it has ext2 file system on it. Even after formatting it with ext3

but why cant I open /dev/sdf?

This seam to be an unusual problem. I can only find 1 page on the internet reference to this problem (sdf) and it happens to be a /dev/sdf/ drive as well. searching for sda,sdb, etc gives no pages on goggle.

I can live with starting from scratch, but it would be sad and it would be allot of work to rip all my DVD´s again.

---

### Post by fjgaude on 2009-02-03
Gosh man... I think you are in deep trouble trying to save you data.

Everytime you use --create you mess up any data that might be left on the remaining healthy drives, two maybe.

Use --assemble using on two drives at a time and see what happens, the two you think might be good.

Good luck!

---

### Post by Fredrik_b on 2009-02-04
I started the computer with live cd (usb) Ubuntu 8.04 desktop.

I can now start mdx with 3 out of 4 disks. but when I try to mount it it ask for a file system, and I dont remember this command. (will googe for it)

The big problem is that the computer freezes when I tried to mount mdx.

The computer seam to be stable when I don't mess around with the raid 5 array.

The raid 1 array is completely stable.

I only have a few files that would be good to save from the array everything ells is media I can replace. 

This is my last attempt if I cant mount it I will try the reformat all drives and start from the beginning. Most likely I have destroyed to much information to be able to get the array upp but it is an learnign experiment.

 
If I start from zero, what is the best way to wipe all info from the drives, so it looks completely new to the system?

---

### Post by fjgaude on 2009-02-04
I trust you have read:

[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

Okay, first stop the array:

```
sudo mdadm --stop /dev/md3
```

or whatever the array name is. If you can't stop it, then umount it:

```
sudo umount /dev/md3
```

Then you have to zero the superblocks on each drive:

```
sudo mdadm --zero-superblock /dev/sdc
```

then sdd, sde, sdf, or whatever the names are.

Please understand all the options and commands before making a new array. After the array is created anew, you have to make the filesystem:

```
sudo mkfs -t ext3 /dev/md3
```

Or whatever the array is now called.

After you add data to the array, please make backups of all important data. I have three, one online, another near-line, and finally, one off-line.

---

### Post by Fredrik_b on 2009-02-07
Thanks for all the help, I have now started from scratch. The problem seam to have been  that one of the sata cables was partly broken, not enough to make the sytem not find the hard drive or make the system think it was anything wrong with the drive. But enough to make it impossible to rebuild the raid array. After I replaced the sata cable everything worked.

So the bottom line, if I had replaced the cable from the beginning i would have saved several days of work.

---

### Post by fjgaude on 2009-02-07
> **Fredrik_b said:**
> Thanks for all the help, I have now started from scratch. The problem seam to have been  that one of the sata cables was partly broken, not enough to make the sytem not find the hard drive or make the system think it was anything wrong with the drive. But enough to make it impossible to rebuild the raid array. After I replaced the sata cable everything worked.

So the bottom line, if I had replaced the cable from the beginning i would have saved several days of work.

Crazy, eh? We learn something new everyday... glad you are on your way.

---

