---
title: "mdadm boot problems"
date: 2009-02-22
forum: General Help
---

### Post by Wonslung on 2009-02-22
i keep getting an checkfs error when i boot that says an error has occured and it can't find some of my filesystem, heres the log



Log of fsck -C -R -A -a
Sun Feb 22 04:52:06 2009

fsck 1.41.3 (12-Oct-2008)
/sbin/fsck.xfs: UUID=cec547d8-bb56daf4-cf7cba6b:ed693cc5 does not exist
fsck died with exit status 8

Sun Feb 22 04:52:06 2009
----------------

what i don't underdstand is if i hit control D and continue the system starts but it doesn't mount /dev/md0 (because it couldnt' find it and the uuid is wrong right?)

but when i do a mdadm --detail --scan /dev/md0 i get this

mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jan  7 19:01:36 2009
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Feb 22 05:09:59 2009
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : cec547d8:bb56daf4:cf7cba6b:ed693cc5
         Events : 0.1491059

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       33        5      active sync   /dev/sdc1



so what the heck is going on? i have to manually mount /dev/md0 every time i reboot...this is annoying

---

### Post by fjgaude on 2009-02-22
One thing, the array may not be fully assembled by the time fsck is invoked. You might try putting in a delay like so, to to stop a race condition with kernel **md**, by editing /init file and adding the sleep line:

<editor> /usr/share/initramfs-tools/init
   
```
   187 maybe_break mount
   188 sleep 10
   189 log_begin_msg "Mounting root file system..."
```

You might try shorter or longer sleep values if it works or doesn't work. Make sure you add the line to the "mount" area. Also the line numbers may be different in your setup than mine.

Now run to rebuild the image:

```
sudo /usr/sbin/update-initramfs -uk all
```

Let us know how you are doing.

---

### Post by Wonslung on 2009-02-22
i've been googling this issue and i've noticed a lot of people refering to /etc/init.d/mdadm-raid which i don't seem to have.....i have /etc/init.d/mdadm 

is this the same thing in ubuntu 8.10?  if not where do i get the correct file

---

### Post by Wonslung on 2009-02-22
I read some stuff online about fixing this and everything i've tried failed...it seems checkfs is happening before the raid can come up....i added mdadm -A -s to /etc/init.d/mountall per a recommendation in the forums....it didn't solve the issue though it seems that if i could somehow make checkfs happen later i'd be ok
i also tried your sleep idea, no beans
here is all i can see on my log screen

i don't know how to log this so i just typed it up so anything that came before it is lost to me



* Setting kernel variables (/etc/sysctl.conf)...			 [OK]
* Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...   [OK]
* Setting kernel variables (/etc/sysctl.d/10-process-security.conf)...   [OK]
* Activating Swap...							 [OK]
* Checking root file system...
fsck 1.41.3 (12-Oct-2008)
/dev/sdg1: clean,   114635/491520 files,  916283/1963938 blocks
									 [OK]
* Starting MD monitoring service mdadm --monitor
mdadm: metadeta format  00:90 unknown, ignored.
mdadm: No mail address or alert command - not monitoring.
								       [fail]
* Checking file systems...
fsck 1.41.3 (12-Oct-2008)
/sbin/fsck.xfs:  UUID=cec547d8-bb56daf4-cf7cba6b:ed693cc5 does not exist
fsck died with exit status 8
								       [fail]
* File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot
bash: no job control in this shell
root@wonslung-raid:~#



any help would be appreciated

---

### Post by fjgaude on 2009-02-22
> /sbin/fsck.xfs: UUID=cec547d8-bb56daf4-cf7cba6b:ed693cc5 does not exist

Is this UUID the mount UUID for the array or the UUID for any one of the drives within the array?

Can you show us your fstab file contents?

---

### Post by Wonslung on 2009-02-22
> **fjgaude said:**
> Is this UUID the mount UUID for the array or the UUID for any one of the drives within the array?

Can you show us your fstab file contents?

  GNU nano 2.0.7                             File: /etc/fstab                                                                

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=41f6e17f-497a-4818-9ada-cabf0e1f8533 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=44cf4dfe-da57-45e8-be3a-1f9f00818d5e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#raid 5
UUID=cec547d8-bb56daf4-cf7cba6b:ed693cc5 /mnt/raid      xfs     relatime        0       1





it's the uuid of /dev/md0

see, heres my mdadm --detail /dev/md0 

wonslung@wonslung-raid:~$ sudo mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jan  7 19:01:36 2009
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Feb 22 23:24:24 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : cec547d8:bb56daf4:cf7cba6b:ed693cc5
         Events : 0.1491059

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       33        5      active sync   /dev/sdc1

---

### Post by fjgaude on 2009-02-23
> #raid 5
UUID=cec547d8-bb56daf4-cf7cba6b:ed693cc5 /mnt/raid xfs relatime 0 1


This line is what is causing the issues, try this:

```
#raid 5
/dev/md0 /mnt/raid xfs defaults 0 2

```

Using "1" for a non-boot drive usually isn't done. And the UUID you are using is not the one that is the mount UUID but the superblock telling mdadm which drives belong in the array... bad, bad, bad. <smile>

Using **blkid** on the system will show what the mount UUID of the array is. Try it and see.

```
sudo blkid
```

You will see that all the drives in the array have the same UUID and that the array itself has another UUID, which is not like the drives.

---

### Post by Wonslung on 2009-02-24
thank you, i didn't know that at all...i'm new to linux and even less experienced with mdadm.....thanks for your help, i'm going to try it now and report back.

---

### Post by Wonslung on 2009-02-24
ok, noticed something VERY fishy...check this out
when i do blkid

wonslung@wonslung-raid:~$ sudo blkid
[sudo] password for wonslung: 
/dev/sda1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sda2: UUID="9bdf903c-e905-0aaf-6883-67f0aabffa7a" TYPE="mdraid" 
/dev/sda3: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 

/dev/sdb1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdb2: UUID="9bdf903c-e905-0aaf-6883-67f0aabffa7a" TYPE="mdraid" 
/dev/sdb3: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdc1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdc2: UUID="33ee9892-a645-4166-8f90-5726ed04f57d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="5679aa57-59a8-48b0-b249-86fac03a03ad" 
/dev/sdc6: UUID="80241ca4-910d-4a32-9d36-7d597a093bcd" TYPE="xfs" 
/dev/sdd1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdd2: UUID="9bdf903c-e905-0aaf-6883-67f0aabffa7a" TYPE="mdraid" 
/dev/sdd3: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sde1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdf1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdf2: UUID="9bdf903c-e905-0aaf-6883-67f0aabffa7a" TYPE="mdraid" 
/dev/sdf3: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdg1: UUID="41f6e17f-497a-4818-9ada-cabf0e1f8533" TYPE="ext3" 
/dev/sde2: UUID="9bdf903c-e905-0aaf-6883-67f0aabffa7a" TYPE="mdraid" 
/dev/sde3: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdg5: TYPE="swap" UUID="44cf4dfe-da57-45e8-be3a-1f9f00818d5e" 
/dev/md0: UUID="a90ef974-55c3-44ff-ac37-40a0b182576e" TYPE="xfs" 
/dev/md1: TYPE="swap" 
/dev/md2: UUID="a90ef974-55c3-44ff-ac37-40a0b182576e" TYPE="xfs" 




it's listing stuff i don't have.....it's showing 3 raid devices...i don't have 3 raids...now i DID have 3 raid devices on the harddrives that the raid is on but never in the current system (it came out of a system with 2 raid 1's and a raid 5 on the devices....a raid 1 for /boot     a raid 1 for swap and the raid 5 for everything else but before i ever put it in this system i got rid of the 2 other raids and grew the raid 5....so i don't know why it's showing up.....)
anyways, how do i fix this



edit

figured this out using the helpfile in blkid
ran sudo blkid -g and it solved the issue

wonslung@wonslung-raid:~$ sudo blkid -g
wonslung@wonslung-raid:~$ sudo blkid
/dev/sda1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdb1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdc1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdd1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sde1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdf1: UUID="d847c5ce-f4da-56bb-6bba-7ccfc53c69ed" TYPE="mdraid" 
/dev/sdg1: UUID="41f6e17f-497a-4818-9ada-cabf0e1f8533" TYPE="ext3" 
/dev/sdg5: TYPE="swap" UUID="44cf4dfe-da57-45e8-be3a-1f9f00818d5e" 
/dev/md0: UUID="a90ef974-55c3-44ff-ac37-40a0b182576e" TYPE="xfs" 
wonslung@wonslung-raid:~$


final edit:
Thanks   It's working..i had no idea there could be more than uuid....anyways, thanks for your help.

---

### Post by fjgaude on 2009-02-24
Seems the **man** pages for **mdadm** would have a big caution somewhere telling about the array UUID versus the mount UUID. Maybe it does but most folks miss reading it.

Wish you would have told us that the drives had been used in other software raid setups. Anyway, you used **blkid -g** to clear the cache.

Great you got the array up and running... the learning curve sometimes is large, eh?

---

### Post by Wonslung on 2009-02-24
yah, i'm sorry, i guess that would have been important info...i'm learning it pretty quick...it's one of the main things i love about linux...it just seems so much more powerful...it's a lot to learn and it seems like theres not always one way to do something.

most of the issues i've had i've had no problem figuring out via google but this one took some real help and i appreciate yours. 

Anyways, thanks...I appreciate your patience and willingness to help.

---

### Post by crimsondr on 2012-03-28
Hi all,

I recently installed a new server with Ubuntu 10.04 and have a couple raid devices.  But on 80% of reboots I would run into the not ready error.  Adding the delay suggestion below fixed it!  The server now boots properly 100% of the time.

Thanks!

> **fjgaude said:**
> One thing, the array may not be fully assembled by the time fsck is invoked. You might try putting in a delay like so, to to stop a race condition with kernel **md**, by editing /init file and adding the sleep line:

<editor> /usr/share/initramfs-tools/init
   
```
   187 maybe_break mount
   188 sleep 10
   189 log_begin_msg "Mounting root file system..."
```

You might try shorter or longer sleep values if it works or doesn't work. Make sure you add the line to the "mount" area. Also the line numbers may be different in your setup than mine.

Now run to rebuild the image:

```
sudo /usr/sbin/update-initramfs -uk all
```

Let us know how you are doing.

---

