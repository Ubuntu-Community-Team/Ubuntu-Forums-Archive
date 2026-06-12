---
title: "Partitions messed up"
date: 2009-01-15
forum: General Help
---

### Post by Criminal.Sausage on 2009-01-15
First of all Hello Everyone :)

Last year I tried installing windows on my Ubuntu box. I edited the partition table with the gparted live disk and formatted the new formed partition to FAT. Everything went well.

Then, when trying to install windows, it said it cannot install on that partition and that it should be formatted. So I let the installer format, yet it didn't help. After retrying a couple of times I decided it was futile.

When booting back into Ubuntu and checking the partition table in gparted the system thought I only had one EMPTY partition (so including the one the program itself was running from..). Live disk has the same problem.

fdisk -l gives the right output.

What is wrong and how can I 'restore' my partition table?
and most of all (and I'm terribly sorry for asking, I need it for school): how can I install windows on /dev/sda5?

Many thanks in advance!


Eric

PS: screenie is Gparted and fdisk -l output.

---

### Post by redilyn on 2009-01-16
I hope someone can answer you gparted question. I've never seen that before.

But to install windows, when you start the install and get to the partition screen, why not delete the FAT partition and then tell windows to install in the unpartitioned space??

---

### Post by caljohnsmith on 2009-01-16
Instead of posting a screen shot, would you please post the output of the following commands:
```
sudo fdisk -lu
sudo sfdisk -d
```
From the screen shot you posted, unfortunately it is clear that your partition table is corrupt, because your sda4 swap partition is inside of your sda3 extended partition; so sda4 should be a logical partition instead, or the sda3 extended partition should end before the sda4 partition begins. That would explain why gparted can't deal with the partition table and instead shows the drive as unallocated. But the good news is that it probably won't be too difficult to fix.

---

### Post by Slim Odds on 2009-01-16
Well.... 

Windows is extremely picky. I must be installed on a **primary **partition. Your FAT is in an ** extended** partition.

I think that Windows also wants to be on the 1st partition.

It's really difficult to install Windows **after** anything else. It's best to partition with the Windows first and primary. Install Windows first and then go from there.

---

### Post by Criminal.Sausage on 2009-01-17
> **caljohnsmith said:**
> Instead of posting a screen shot, would you please post the output of the following commands:
```
sudo fdisk -lu
sudo sfdisk -d
```
From the screen shot you posted, unfortunately it is clear that your partition table is corrupt, because your sda4 swap partition is inside of your sda3 extended partition; so sda4 should be a logical partition instead, or the sda3 extended partition should end before the sda4 partition begins. That would explain why gparted can't deal with the partition table and instead shows the drive as unallocated. But the good news is that it probably won't be too difficult to fix.

Output for fdisk -lu
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06e858c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   359454374   179727156   83  Linux
/dev/sda2       359454375   361141199      843412+  83  Linux
/dev/sda3       361141200   488392064    63625432+   5  Extended
/dev/sda4       482335623   488392064     3028221   82  Linux swap / Solaris
/dev/sda5       361141263   480809384    59834061    e  W95 FAT16 (LBA)
/dev/sda6       480809448   482335559      763056   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 21 sectors/track, 4334 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064     7827455     3909696    c  W95 FAT32 (LBA)
```

Output for sfdisk -d
```
 sausage@Pwn-b0x:~$ sudo fdisk -lu
[sudo] password for sausage: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06e858c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   359454374   179727156   83  Linux
/dev/sda2       359454375   361141199      843412+  83  Linux
/dev/sda3       361141200   488392064    63625432+   5  Extended
/dev/sda4       482335623   488392064     3028221   82  Linux swap / Solaris
/dev/sda5       361141263   480809384    59834061    e  W95 FAT16 (LBA)
/dev/sda6       480809448   482335559      763056   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 21 sectors/track, 4334 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064     7827455     3909696    c  W95 FAT32 (LBA)

```

Few more things:
Redilyn: Already tried what you suggested before. Unfortunately it didn't work.
Slim Odds: I'm not quite sure what you mean. Do you mean that I have to erase my entire disk?


Anyways, Thanks for the help all of you!

Eric

---

### Post by caljohnsmith on 2009-01-17
I just thought I would mention first that you have two swap partitions, when really you only need one. Multiple distros can even share the same swap partition, so you don't need more than one swap partition. But to correct your partition problem, how about doing:
```
sudo parted -s /dev/sda rm 4 > /dev/null
```
That should get rid of the offending sda4 swap partition. Then reboot, and post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted -l

```
If the last parted command does not report any errors, go ahead and run gparted again, and you can resize your remaining sda6 swap partition to be 3 GB like sda4 was if you want, or whichever size you prefer. You'll probably need to first right-click the swap partition in gparted and select "swapoff" in order to make any changes. Once you are done, how about posting:
```
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
sudo blkid -c /dev/null
```
And we can work from there if you want.

---

### Post by louieb on 2009-01-17
> **Slim Odds said:**
> ...Windows is extremely picky. I must be installed on a **primary **partition. Your FAT is in an ** extended** partition.

Slim is mostly right. Windows does not install happily in a logical partition. It can be done but to do it another version of windows has to be installed in a primary partition 1st.

As **caljohnsmith 	 		**points out the partition table does not follow the rules. I've seen some Linux distro installers and windows partitioner's modify a partiton table that way. PC still works. But Gparted and the Ubuntu installer will not work on that drive.

Post the output **caljohnsmith** asked for. If anybody can show you how to get it fixed without doing a complete wipe of the drive and reinstalling everything - he can. I'm going to watch this theard with great intrest.

---

### Post by Criminal.Sausage on 2009-01-18
Hi Everybody, again thanks for the replies:)

> **caljohnsmith said:**
> But to correct your partition problem, how about doing:
```
sudo parted -s /dev/sda rm 4 > /dev/null
```
That will get rid of the offending sda4 swap partition.

The output of sudo parted -s /dev/sda rm 4 > /dev/null:
```
sausage@Pwn-b0x:~$ sudo parted -s /dev/sda rm 4 > /dev/null
Error: Can't have overlapping partitions.
```

Guess it didn't work out the way it was supposed to?

Anyway, thanks for the help^^

Eric

---

### Post by caljohnsmith on 2009-01-18
OK, how about posting again:
```
sudo fdisk -lu
sudo sfdisk -d
```
Previously you posted fdisk twice, so please make sure to post the sfdisk command above if you can.

---

### Post by Criminal.Sausage on 2009-01-18
> **caljohnsmith said:**
> OK, how about posting again:
```
sudo fdisk -lu
sudo sfdisk -d
```
Previously you posted fdisk twice, so please make sure to post the sfdisk command above if you can.


WHoa lightning fast reply!
I must have been partially sleeping when posting the outputs, sorry.

again- fdisk -lu
```
sausage@Pwn-b0x:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06e858c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   359454374   179727156   83  Linux
/dev/sda2       359454375   361141199      843412+  83  Linux
/dev/sda3       361141200   488392064    63625432+   5  Extended
/dev/sda4       482335623   488392064     3028221   82  Linux swap / Solaris
/dev/sda5       361141263   480809384    59834061    e  W95 FAT16 (LBA)
/dev/sda6       480809448   482335559      763056   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 21 sectors/track, 4334 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

```

sfdisk -d:
```
sausage@Pwn-b0x:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=359454312, Id=83, bootable
/dev/sda2 : start=359454375, size=  1686825, Id=83
/dev/sda3 : start=361141200, size=127250865, Id= 5
/dev/sda4 : start=482335623, size=  6056442, Id=82
/dev/sda5 : start=361141263, size=119668122, Id= e
/dev/sda6 : start=480809448, size=  1526112, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     8064, size=  7819392, Id= c
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

```


Eric

---

### Post by caljohnsmith on 2009-01-18
OK, how about first downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output so I can check that everything went OK. Also, the above command will create a backup of the sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so that if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. Next reboot, and please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
sudo blkid -c /dev/null
```
Also, in case anyone is interested, for convenience here is the contents of the partition_table.txt file:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=359454312, Id=83, bootable
/dev/sda2 : start=359454375, size=  1686825, Id=83
/dev/sda3 : start=361141200, size=127250865, Id= 5
[COLOR="Red"]/dev/sda4 : start=        0, size=        0, Id= 0[/COLOR]
/dev/sda5 : start=361141263, size=119668122, Id= e
/dev/sda6 : start=480809448, size=  1526112, Id=82
```
So basically all I did was delete the offending sda4 swap partition and keep the sda6 swap partition instead, since only one swap partition is necessary. :)

---

### Post by Criminal.Sausage on 2009-01-18
Hi caljohnsmith!
here are the outputs you asked for.

```
sausage@Pwn-b0x:~$ sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
[sudo] password for sausage: 
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  22374   22375- 179727156   83  Linux
/dev/sda2      22375   22479     105     843412+  83  Linux
/dev/sda3      22480   30400    7921   63625432+   5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      22480+  29928    7449-  59834061    e  W95 FAT16 (LBA)
/dev/sda6      29929+  30023      95-    763056   82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 359454374  359454312  83  Linux
/dev/sda2     359454375 361141199    1686825  83  Linux
/dev/sda3     361141200 488392064  127250865   5  Extended
/dev/sda4             0         -          0   0  Empty
/dev/sda5     361141263 480809384  119668122   e  W95 FAT16 (LBA)
/dev/sda6     480809448 482335559    1526112  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

```
sausage@Pwn-b0x:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06e858c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   359454374   179727156   83  Linux
/dev/sda2       359454375   361141199      843412+  83  Linux
/dev/sda3       361141200   488392064    63625432+   5  Extended
/dev/sda5       361141263   480809384    59834061    e  W95 FAT16 (LBA)
/dev/sda6       480809448   482335559      763056   82  Linux swap / Solaris
``````

sausage@Pwn-b0x:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=359454312, Id=83, bootable
/dev/sda2 : start=359454375, size=  1686825, Id=83
/dev/sda3 : start=361141200, size=127250865, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=361141263, size=119668122, Id= e
/dev/sda6 : start=480809448, size=  1526112, Id=82

```

```
sausage@Pwn-b0x:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f920abe3-4e23-4c61-829e-60eacf16f07b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9b6dee5c-7848-43f3-a203-3e762966b7bf none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
```
sausage@Pwn-b0x:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=9b6dee5c-7848-43f3-a203-3e762966b7bf

``````
/dev/sda1: UUID="f920abe3-4e23-4c61-829e-60eacf16f07b" TYPE="ext3" 
/dev/sda2: UUID="a82bf2fc-f61e-4998-8af5-33a4f5e623f1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="bcf00d9b-4362-4f56-8d93-76f8585af25b" 

```

Thanks again!

---

### Post by caljohnsmith on 2009-01-18
Great, it looks like everything went OK. Do you want a larger swap partition than its current size of 760 MB? If so, it would be good to resize the swap partition before proceeding. Next do:
```
sudo mkswap -U 9b6dee5c-7848-43f3-a203-3e762966b7bf /dev/sda6
```
Then reboot, and please post the new output of:
```
sudo blkid -c /dev/null
free
```
And we can work from there. :)

---

### Post by Criminal.Sausage on 2009-01-18
To be honest with you: I have no idea what the swap is. I do not have any stability or performance issues. But I guess it has some use. I resized it to 1 GB.

```
sausage@Pwn-b0x:~$ sudo blkid -c /dev/null
[sudo] password for sausage: 
/dev/sda1: UUID="f920abe3-4e23-4c61-829e-60eacf16f07b" TYPE="ext3" 
/dev/sda2: UUID="a82bf2fc-f61e-4998-8af5-33a4f5e623f1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="9b6dee5c-7848-43f3-a203-3e762966b7bf" 
sausage@Pwn-b0x:~$ 

``````
sausage@Pwn-b0x:~$ free
             total       used       free     shared    buffers     cached
Mem:       1034236     691056     343180          0      18404     347796
-/+ buffers/cache:     324856     709380
Swap:      1052216          0    1052216

```

Eric

---

### Post by caljohnsmith on 2009-01-18
OK, it looks like everything went just fine and your Linux partition is now using the new swap partition. But I must apologize, because I see we took an unnecessary (although perfectly harmless) step of getting your swap partition working; after reading your first post again, I realized that probably the best thing to do now that your partition table is fixed would be to delete the sda6 swap partition and the sda5 FAT partition (and also the sda3 extended partition container), because as louieb all ready pointed out, you won't be able to install Windows to a logical partition unless you have a primary NTFS/FAT partition available where Windows can put its boot files. Once sda3, sda5 and sda6 are deleted, you can create a primary NTFS partition for Windows, and then recreate the swap partition as either a primary partition or as a logical partition inside of an extended partition again. 

So the bottom line is that I would boot up your Live CD, run gparted, right-click the swap partition and select "swapoff", delete the swap partition, the FAT partition and also the sda3 extended partition, create a new primary NTFS partition for Windows right after the sda2 partition. And then with the remaining space on the drive, create an extended partition, and inside of the extended partition create your swap partition again. Once you have all the partitions set up OK, when you boot back into Ubuntu you'll need to run the "mkswap" command from post #13 on whichever is your new swap partition (be sure to use the correct /dev/sdaX partition) in order for Ubuntu to use the new swap partition. Good luck and let us know how it goes or if you run into problems. :)

---

### Post by Criminal.Sausage on 2009-01-19
Everything seems to be allright now. The partitions are created (with a primary ntfs) and ubuntu recognised the swap.
Only thing keeping me from installing windows now is that I can't find my installation disc. I will post if I succeeded in installing XP. For now there isn't really anything to do except for searching..

Anyway, many thanks for your help caljohnsmith! I really appreciate it!

Cheers,

Eric

---

### Post by caljohnsmith on 2009-01-19
Glad to hear the repartioning was successful, so at least the only thing left is to find your XP Install CD. You are probably all ready aware of this, but I just thought I would mention that installing XP will overwrite Grub in the MBR (Master Boot Record); so to restore Grub after installing XP, you could do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Anyway, good luck, and hope the XP installation goes smoothly. :)

---

### Post by Criminal.Sausage on 2009-01-19
Thanks for the tip, but indeed I already thought of that:) I've downloaded supergrub live disc. I've used it a couple times before. Does the job well.

--Edit 1:--

Just found my copy of windows. Will install it now. Let's see if your efforts truly paid off!


Regards,

Eric

--Edit 2:--
Everything went fine. Windows is up and running. Thanks for the help!

---

### Post by caljohnsmith on 2009-01-19
You're welcome, I'm glad to hear Windows installed without any problems. Cheers and have fun with Ubuntu and Windows. :)

---

