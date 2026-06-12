---
title: "[SOLVED] File System Hosed?"
date: 2008-12-08
forum: General Help
---

### Post by klausner on 2008-12-08
I've got a Fujitsu laptop that was configured to dual boot Windoze XP and Intrepid 8.10. I had to re-install XP, which, of course, wiped out grub.

I booted from the live CD, and tried to restore grub, and got the following:

> sudo grub

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

So I went to gparted, which reports that the entire disk is "unallocated". This makes no sense, because I can see all the partitions in Nautilus, 

[CENTER][IMG]http://farm4.static.flickr.com/3147/3094805760_856135454c_d.jpg[/IMG][/CENTER]

and if I run fdisk I get:

> sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00134d85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080       19457   123523785    5  Extended
/dev/sda3           18805       19457     5245222+  82  Linux swap / Solaris
/dev/sda5            4080        4210     1052194+  83  Linux
/dev/sda6            4211        4993     6289416   83  Linux
/dev/sda7            4994       10215    41945683+  83  Linux
/dev/sda8           10216       16089    47182873+  83  Linux
/dev/sda9           16090       18804    21808206    b  W95 FAT32

I've also got problems with Windoze crashing repeatedly with the BSOD, despite several re-installs. But that's not an issue for this group. How can I fix the filesystem problem and get grub working again?

---

### Post by meierfra. on 2008-12-09
Try

```
sudo grub
```
and at the grub prompt:

```

find /boot/grub/stage2
```

This will return (hdX,Y), where X and Y are some numbers, like (hd0,6). Use these numbers in the next step:

```
root (hdX,Y)
setup (hdX)
quit
```

Reboot  and hope for the best.

Since your partition tabled is messed up, there is a fair chance  that this will not work.  Then post the output of
 

```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```

for further help.

---

### Post by klausner on 2008-12-10
> **meierfra. said:**
> Try

```
sudo grub
```
and at the grub prompt:

```

find /boot/grub/stage2
```

This will return (hdX,Y), where X and Y are some numbers, like (hd0,6). Use these numbers in the next step:

```
root (hdX,Y)
setup (hdX)
quit
```

Reboot  and hope for the best. Managed

Since your partition tabled is messed up, there is a fair chance  that this will not work.  Then post the output of
 

```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```

for further help.

The good news: I made some progress.Managed to keep windoze up long enough to get PartitionMagic to fix a couple of boot sector errors. When I returned to the live CD, now I can see to disk in gparted and with fdisk -l.

Thw bad news:
> grub> find /boot/grub/stage2

Error 15: File not found

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition


Following your instructions yields:

> sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00134d85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    65529134    32764536    7  HPFS/NTFS
/dev/sda2        65529135   302086259   118278562+   f  W95 Ext'd (LBA)
/dev/sda3       302086260   312576704     5245222+  82  Linux swap / Solaris
/dev/sda5        65529261    67633649     1052194+  83  Linux
/dev/sda6        67633713    80212544     6289416   83  Linux
/dev/sda7        80212608   164103974    41945683+  83  Linux
/dev/sda8       164104038   258469784    47182873+  83  Linux
/dev/sda9       258469848   302086259    21808206    b  W95 FAT32

and

> sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 65529072, Id= 7, bootable
/dev/sda2 : start= 65529135, size=236557125, Id= f
/dev/sda3 : start=302086260, size= 10490445, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 65529261, size=  2104389, Id=83
/dev/sda6 : start= 67633713, size= 12578832, Id=83
/dev/sda7 : start= 80212608, size= 83891367, Id=83
/dev/sda8 : start=164104038, size= 94365747, Id=83
/dev/sda9 : start=258469848, size= 43616412, Id= b


So at least I can get to my files, but I still can't boot to Linux from the hard disk :frown:

---

### Post by meierfra. on 2008-12-10
Very strange, the output id "fdisk -l" from post 1 does not match the output of "fdisk -lu" from post 3.   Did you you do anything which could have changed your partition table since your first post?


Try this to fix your partition table:

```
sudo sfdisk -d /dev/sda | sudo --force sfdisk /dev/sda 
```

(this will produce a bunch of output, which you can ignore. But just for double checking, post it here)

Then look at 

```
sudo fdisk -lu
```

You should get the exact same output as in your last post, except that "omitting empty partition (5)" should be gone.


Then  try to reinstall grub again (see post 2), but this time  add one line
after "find /boot/grub/stage2"

```

find /grub/stage2

```

One of the  two "find ..." commands  should return (hdX,Y), and the other "error 15, file not found.

---

### Post by klausner on 2008-12-10
> **meierfra. said:**
> Very strange, the output id "fdisk -l" from post 1 does not match the output of "fdisk -lu" from post 3.   Did you you do anything which could have changed your partition table since your first post?


Try this to fix your partition table:

```
sudo sfdisk -d /dev/sda | sudo --force sfdisk /dev/sda 
```

(this will produce a bunch of output, which you can ignore. But just for double checking, post it here)

Then look at 

```
sudo fdisk -lu
```

You should get the exact same output as in your last post, except that "omitting empty partition (5)" should be gone.


Then  try to reinstall grub again (see post 2), but this time  add one line
after "find /boot/grub/stage2"

```

find /grub/stage2

```

One of the  two "find ..." commands  should return (hdX,Y), and the other "error 15, file not found.

The changes to /dev/sda2 (which is what I assume you are referring to) are probably the changes made by PartitionMagic.

The output from *sudo sfdisk -d /dev/sda* is

> # partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 65529072, Id= 7, bootable
/dev/sda2 : start= 65529135, size=236557125, Id= f
/dev/sda3 : start=302086260, size= 10490445, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 65529261, size=  2104389, Id=83
/dev/sda6 : start= 67633713, size= 12578832, Id=83
/dev/sda7 : start= 80212608, size= 83891367, Id=83
/dev/sda8 : start=164104038, size= 94365747, Id=83
/dev/sda9 : start=258469848, size= 43616412, Id= b

I assume you mean to use *sudo **sfdisk --force** /dev/sda* rather than ***sudo --force** sfdisk /dev/sda*. I didn't execute this, because I don't want to lose the current contents of the disk. Will that be the result?

I did try *find /grub/stage2* in grub, and get:

> (hd0,5)

---

### Post by meierfra. on 2008-12-10
> I assume you mean to use sudo sfdisk --force /dev/sda rather than sudo --force sfdisk /dev/sda. 

Yes, I did.

> didn't execute this, because I don't want to lose the current contents of the disk. Will that be the result?

No, it will not effect any of your data.  It will  fix your partition table.  Currently your partition table contains an  empty partition. (That is  a partition of size 0).  
Different programs deal with empty partitions in different ways:

fdisk just ignores them:  omitting empty partition (5)

empty partitions do not have a corresponding device,  so none of the devices /dev/sda1 to /dev/sda9 are linked to the empty partition.  

grub treats them like real partitions:  "find /grub/stage2" returned (hd0,5). Grub starts counting at zero, so (hd0,5)  usually refers to /dev/sda6.
But "stage2" is really on your 1Gb boot partition  /dev/sda5.  So  "find /grub/stage2" should return (hd0,4).  But  grub assigns (hd0,4)  to the empty partition.

gparted  (the partition editor) does not know how to deal with empty partitions, it probably will  show your whole drive as unallocated.


You might be able to leave the partition table as it is and  reinstall grub  via

```
sudo grub
root (hd0,5)
setup (hd0)
quit
```


But it would be better to remove the empty partition from the partition table. Since "sfdisk" ignores the empty partition "sfdisk -d /dev/sda" actually  produces the correct partition table. So the first half of the command


```
sudo sfdisk -d /dev/sda | sudo  sfdisk  --force /dev/sda
```

spits out the correct partition table, the second half  then writes this partition table to your hard drive. (Note that this is just one command, do not press enter after the first half)


Once you run this command, "fdisk -lu" should not complain  abut an  empty partition any more and "gparted should show all your partitions again.
Also "find /boot/grub/stage2" at the grub prompt will now return (hd0,4) and you can reinstall grub with

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

---

### Post by klausner on 2008-12-11
That solved it. Thank you for your time and patience.

---

### Post by meierfra. on 2008-12-11
> That solved it. Thank you for your time and patience.

You are welcome. Have fun with Ubuntu and Windows.

---

### Post by klausner on 2008-12-11
> **meierfra. said:**
> You are welcome. Have fun with Ubuntu and Windows.

Thanks again. Ubuntu is fine now. @#$%^&* Windoze is still crashing, but that's not a problem for this group.

---

