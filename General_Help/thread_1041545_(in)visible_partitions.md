---
title: "(in)visible partitions"
date: 2009-01-16
forum: General Help
---

### Post by tubunu on 2009-01-16
I have a very strange problem. 

Was double booting Win/Ubuntu but Windows got some virus so I had to make a clean install of it. To my surprise Ubuntu root (/) directory is gone now so I can't boot into Linux. /home and /swap directories are still there. 

I've decided to reinstall Ubuntu, but the partition I want to install it on shows up as entirely **unallocated** even though there's a fresh windows install on it, my /home partition and /swap. 

If I go ahead and create partitions on it, it will most likely format my windows and /home partitions and I don't want that!!! What can I do? Please advise. Thank you. 

I'm running a live CD now and here's my fdisk -l output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4866    39086113+   7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f9134d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3038    24402703+   7  HPFS/NTFS
/dev/sdb2            3039       15091    96815722+   7  HPFS/NTFS
/dev/sdb3           15092       18728    29214202+   5  Extended
/dev/sdb4           15157       18728    28692090   83  Linux
/dev/sdb5           15092       15156      522049+  82  Linux swap / Solaris

```

Windows C is on /dev/sdb1. My /home partition is /dev/sdb4. I can't lose these! Why oh why disk **sdb** shows up as unallocated in Ubuntu install wizard? :(

---

### Post by tubunu on 2009-01-16
Here's a screenshot to make it easier to understand.

---

### Post by theWrkncacnter on 2009-01-16
I'm actually having a problem similar to this -- there's a neat program called TestDisk that can find and restore lost/hidden partitions. See my thread if it helps using it: [http://ubuntuforums.org/showthread.php?t=1038880](http://ubuntuforums.org/showthread.php?t=1038880)
Hope that helps!

---

### Post by tubunu on 2009-01-16
OK, thanks a lot, theWrkncacnter. Here's what I get with TestDisk:

```
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3037 254 63   48805407
 2 P HPFS - NTFS           3038   0  1 15090 254 63  193631445 [data]
 3 E extended             15091   0  1 18727 254 63   58428405
 4 P Linux                15156   0  1 18727 254 63   57384180
Space conflict between the following two partitions
 3 E extended             15091   0  1 18727 254 63   58428405
 4 P Linux                15156   0  1 18727 254 63   57384180
   X extended             15091   0  2 15155 254 63    1044224
 5 L Linux Swap           15091   2  1 15155 254 63    1044099





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition


```

I don't know what to do next. Proceed or backup? I don't understand that "space conflict" thing..

---

### Post by taurus on 2009-01-16
Why don't you try to unmount all the partitions in /dev/sdb before you fire up gparted?

---

### Post by tubunu on 2009-01-16
> **taurus said:**
> Why don't you try to unmount all the partitions in /dev/sdb before you fire up gparted?

I've just unmounted all the partitions and gparted shows unallocated space again. No change. :confused:

---

### Post by theWrkncacnter on 2009-01-16
I think the next thing to do is examine each partition in testdisk with "p" to see which partitions have directories. These are the real partitions. Post back with which partitions give you directory listings. Then we can try to figure out what to do with testdisk.

---

### Post by tubunu on 2009-01-16
Okay, here are directory listings of: 

```

Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3037 254 63   48805407
D HPFS - NTFS           3038   0  1 15090 254 63  193631445 [data]
D Linux Swap           15091   2  1 15155 254 63    1044099
D Linux                15156   0  1 18727 254 63   57384180
D Linux                18728   0  1 19456 254 63   11711385

```

The first and the second NTFS give me this result with "p": ubuntu@ubuntu:~$ GiB
These are my Windows partitions which do work when I boot Windows.

The fourth (Linux) which I recognize as my /home partition:
```
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 .
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 ..
drwx------     0     0     16384 30-Jul-2007 22:29 lost+found
lrwxrwxrwx     0     0        44 30-Jul-2007 22:30 .directory
drwxr-xr-x  1000  1000     16384  9-Jan-2009 21:57 di

```

And the fifth (Linux) which I recognize as my missing / partition:
```

drwxr-xr-x     0     0      4096  2-Jan-2009 22:03 .
drwxr-xr-x     0     0      4096  2-Jan-2009 22:03 ..
drwx------     0     0     16384 25-Apr-2008 15:44 lost+found
drwxr-xr-x     0     0      4096 22-Apr-2008 18:07 var
drwxr-xr-x     0   999      4096 25-Apr-2008 15:44 home
drwxr-xr-x     0   999      4096 25-Apr-2008 15:44 windows
drwxr-xr-x     0     0     12288  9-Jan-2009 21:57 etc
drwxr-xr-x     0     0      4096  9-Jan-2009 18:04 media
lrwxrwxrwx     0     0        11 25-Apr-2008 15:45 cdrom
drwxr-xr-x     0     0      4096 18-Dec-2008 22:53 bin
drwxr-xr-x     0     0      4096 17-Dec-2008 15:35 boot
drwxr-xr-x     0     0     12288 24-Oct-2008 23:23 dev
drwxr-xr-x     0     0      4096 22-Apr-2008 17:48 initrd
drwxr-xr-x     0     0     12288  7-Jan-2009 23:03 lib
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 mnt
drwxr-xr-x 10490    25      4096  2-Jan-2009 22:03 opt
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 proc
drwxr-xr-x     0     0      4096 20-Dec-2008 18:09 root
drwxr-xr-x     0     0      4096 18-Dec-2008 22:53 sbin
drwxr-xr-x     0     0      4096 22-Apr-2008 17:48 srv
drwxr-xr-x     0     0      4096 19-Apr-2008 05:05 sys
drwxrwxrwt     0     0     12288  9-Jan-2009 21:57 tmp
drwxr-xr-x     0     0      4096  4-Nov-2008 14:55 usr
lrwxrwxrwx     0     0        29  1-Dec-2008 20:36 vmlinuz
lrwxrwxrwx     0     0        32  1-Dec-2008 20:36 initrd.img
-rw-------     0     0      1238  2-Jan-2009 22:03 AdobeReader.desktop
lrwxrwxrwx     0     0        27  4-Nov-2008 14:55 initrd.img.old
lrwxrwxrwx     0     0        24  4-Nov-2008 14:55 vmlinuz.old

```

---

### Post by caljohnsmith on 2009-01-16
It looks like your partition table is definitely corrupt. Can you please also post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And in the meantime, try doing the "deep search" with testdisk by following these instructions:

After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. Also, be sure you are using testdisk version 6.9 or later, because otherwise it will most likely crash when you try to list the directory of your NTFS partitions.

---

### Post by tubunu on 2009-01-17
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78172289    39086113+   7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f9134d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    48805469    24402703+   7  HPFS/NTFS
/dev/sdb2        48805470   242436914    96815722+   7  HPFS/NTFS
/dev/sdb3       242436915   300865319    29214202+   5  Extended
/dev/sdb4       243481140   300865319    28692090   83  Linux
/dev/sdb5       242437041   243481139      522049+  82  Linux swap / Solaris

```

```
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78172227, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 48805407, Id= 7, bootable
/dev/sdb2 : start= 48805470, size=193631445, Id= 7
/dev/sdb3 : start=242436915, size= 58428405, Id= 5
/dev/sdb4 : start=243481140, size= 57384180, Id=83
/dev/sdb5 : start=242437041, size=  1044099, Id=82

```

I'm doing deep search as I type this.

---

### Post by tubunu on 2009-01-17
Mmm here's the output of deep search. :confused:

```
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63

The harddisk (160 GB / 149 GiB) seems too small! (< 320 GB / 298 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          19456 254 63 38913 253 62  312576642

```

And it listed some partitions twice..

```
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3037 254 63   48805407
D HPFS - NTFS              0   1  1 19456 254 63  312576642
D HPFS - NTFS           1961   0  1 14013 254 63  193631445 [data]
D HPFS - NTFS           3037 254 63  6075 254 63   48805471
D HPFS - NTFS           3038   0  1 15090 254 63  193631445 [data]
D HPFS - NTFS           3038   0 13 15090 254 63  193631433
D Linux Swap           15091   2  1 15155 254 63    1044099
D Linux                15156   0  1 18727 254 63   57384180
D Linux                18728   0  1 19456 254 63   11711385

```

---

### Post by caljohnsmith on 2009-01-17
> **tubunu said:**
> ```

[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f9134d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    48805469    24402703+   7  HPFS/NTFS
/dev/sdb2        48805470   242436914    96815722+   7  HPFS/NTFS
[COLOR="Red"]/dev/sdb3       242436915   300865319[/COLOR]    29214202+   5  Extended
[COLOR="Red"]/dev/sdb4       243481140   300865319[/COLOR]    28692090   83  Linux
/dev/sdb5       242437041   243481139      522049+  82  Linux swap / Solaris

```

As you can see highlighted in red above, your sdb4 Linux primary partition is inside of your sdb3 extended partition, and since the sda4 partition begins at the sector immediately following the sda5 swap partition, sda4 can't be a logical partition under normal circumstances (or at least in order to be compatible with Windows partitioning software). It looks like the best thing to do would be to correct the ending point of your extended partition instead so that the sda4 partition is not inside of it. So to correct the problem, how about doing:
```
echo "242436915,1044225,5" | sudo sfdisk -fuS /dev/sdb -N3 -O sdb_sectors_modified.save
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output so I can check that everything went OK. Also, the above command will create a backup of the HDD sectors being modified as a small "sdb_sectors_modified.save" file on your desktop, so that if for some reason anything were to go wrong, you can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. Next boot your Live CD again, and post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted -l
```
Next post the output of all the following commands:
```
sudo mount /dev/sdb4 /mnt
cat /mnt/etc/fstab
cat /mnt/etc/initramfs-tools/conf.d/resume
cat /mnt/boot/grub/menu.lst
sudo blkid -c /dev/null
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
And we can work from there.

---

### Post by tubunu on 2009-01-17
Yup, sure. The command gives me an error. After unmounting all sdb partitions it also gives me the same error. Thank you so much caljohnsmith for your input.

EDIT: this info is irrelevant now. No error.

---

### Post by tubunu on 2009-01-17
OK :)

```
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ echo "242436915,1044225,5" | sudo sfdisk -fuS /dev/sdb -N3 -O sdb_sectors_modified.save
Checking that no-one is using this disk right now ...
OK

Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63  48805469   48805407   7  HPFS/NTFS
/dev/sdb2      48805470 242436914  193631445   7  HPFS/NTFS
/dev/sdb3     242436915 243481139    1044225   5  Extended
/dev/sdb4     243481140 300865319   57384180  83  Linux
/dev/sdb5     242437041 243481139    1044099  82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63  48805469   48805407   7  HPFS/NTFS
/dev/sdb2      48805470 242436914  193631445   7  HPFS/NTFS
/dev/sdb3     242436915 243481139    1044225   5  Extended
/dev/sdb4     243481140 300865319   57384180  83  Linux
/dev/sdb5     242437041 243481139    1044099  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

---

### Post by tubunu on 2009-01-17
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78172289    39086113+   7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f9134d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    48805469    24402703+   7  HPFS/NTFS
/dev/sdb2        48805470   242436914    96815722+   7  HPFS/NTFS
/dev/sdb3       242436915   243481139      522112+   5  Extended
/dev/sdb4       243481140   300865319    28692090   83  Linux
/dev/sdb5       242437041   243481139      522049+  82  Linux swap / Solaris

```
```

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78172227, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 48805407, Id= 7, bootable
/dev/sdb2 : start= 48805470, size=193631445, Id= 7
/dev/sdb3 : start=242436915, size=  1044225, Id= 5
/dev/sdb4 : start=243481140, size= 57384180, Id=83
/dev/sdb5 : start=242437041, size=  1044099, Id=82

```
```

ubuntu@ubuntu:~$ sudo parted -l
parted: invalid option -- l
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)      
```

The next set of commands:

```

ubuntu@ubuntu:~$ sudo mount /dev/sdb4 /mnt

```
```

ubuntu@ubuntu:~$ cat /mnt/etc/fstab
cat: /mnt/etc/fstab: No such file or directory

```
```

ubuntu@ubuntu:~$ cat /mnt/etc/initramfs-tools/conf.d/resume
cat: /mnt/etc/initramfs-tools/conf.d/resume: No such file or directory

```
```

ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
cat: /mnt/boot/grub/menu.lst: No such file or directory

```
```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="5DF6BEE60BC014A4" TYPE="ntfs" 
/dev/sdb1: UUID="E674ADAE74AD8243" TYPE="ntfs" 
/dev/sdb2: UUID="7092ADE41FB79F06" LABEL="data" TYPE="ntfs" 
/dev/sdb4: UUID="58bd0420-dbef-4b74-9b7b-de9bedee8e6e" TYPE="ext3" 
/dev/sdb5: UUID="de1aa6a6-0dc0-41fd-9f81-e595fcaf632d" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

```
```

ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
02ff

```

---

### Post by caljohnsmith on 2009-01-17
Great, it looks like correcting the partition table problem went exactly as planned, so you should hopefully be able to use gparted on the drive now without any problems. Do you still want to reinstall Ubuntu? Or do you want to try and salvage your present Ubuntu install? While you still have sda4 mounted on /mnt, please post:
```
ls -l /mnt
```

---

### Post by tubunu on 2009-01-17
I can't make out much of these commands, but I've just checked GParted and it lists ALL my sdb partitions!!!! :) Wow! [B]Thank you so much caljohnsmith. 
[/B]
Does that mean I am safe now to install Ubuntu?

---

### Post by tubunu on 2009-01-17
> **caljohnsmith said:**
> Do you still want to reinstall Ubuntu?

Yes, I would like to make a clean install of Hardy LTS, since I had some minor complaints about Intrepid. 

> **caljohnsmith said:**
>  While you still have sda4 mounted on /mnt, please post:
```
ls -l /mnt
```


```
ubuntu@ubuntu:~$ ls -l /mnt
total 32
drwxr-xr-x 106 1000 1000 16384 2009-01-09 21:57 di
drwx------   2 root root 16384 2007-07-30 22:29 lost+found
ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2009-01-17
> **tubunu said:**
> I can't make out much of these commands, but I've just checked GParted and it lists ALL my sdb partitions!!!! :) Wow! Thank you so much caljohnsmith. 

Does that mean I am safe now to install Ubuntu?
You're welcome, and sure, you should be able to go ahead and reinstall Ubuntu now if that is your plan. Good luck and let me know how it goes. :)

---

### Post by tubunu on 2009-01-17
Here's the first problem... 

The original root partition with my previous Ubuntu install is listed as the very last partition in GParted. When I try to create a new partition there it says "It's not possible to create more than 4 primary partitions" and "If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

In the install wizard that partition is listed as "unusable" and all options are greyed out. :(

---

### Post by caljohnsmith on 2009-01-17
It looks like you need to unmount everything first; how about quiting gparted, and do:
```
cd /
sudo umount /mnt
sudo swapoff -a
```
And then try gparted again. As long as you are reinstalling, I would suggest deleting sda4 and expand the sda2 extended partition to use that space, and then create a logical partition inside of sda2 for your main Ubuntu partition. Let me know how that goes or if you still run into problems.

---

### Post by tubunu on 2009-01-17
> **caljohnsmith said:**
> As long as you are reinstalling, I would suggest deleting sda4 and expand the sda2 extended partition to use that space, and then create a logical partition inside of sda2 for your main Ubuntu partition. Let me know how that goes or if you still run into problems.

Mmm.. sdb4 is my /home partition, I wouldn't like to lose its data if I delete it..

---

### Post by caljohnsmith on 2009-01-17
From the previous results you posted, the sdb4 partition only has a "lost+found" directory, so it doesn't look like your home partition is OK. If you're lucky the lost+found directory may have your home directory personal files. How about posting the output of:
```
sudo mount /dev/sdb4 /mnt
sudo ls -lR /mnt/lost+found
```

---

### Post by tubunu on 2009-01-17
> **caljohnsmith said:**
> If you're lucky the lost+found directory may have your home directory personal files. 

```
ubuntu@ubuntu:/$ sudo mount /dev/sdb4 /mnt
ubuntu@ubuntu:/$ sudo ls -lR /mnt/lost+found
/mnt/lost+found:
total 0

```

Funny thing. I could access all my home dir personal files in sdb4 just before I issued that last command. Now it's gone.. please tell me it's not so.. :confused:

EDIT: Sigh of relief.. I issued umount /dev/sdb4 and it's OK. Yes, I have all my home dir files intact.

---

### Post by ajcham on 2009-01-17
> **caljohnsmith said:**
> From the previous results you posted, the sdb4 partition only has a "lost+found" directory, so it doesn't look like your home partition is OK.

I think you may be mistaken, caljohn:
[QUOTE=tubunu]```
ubuntu@ubuntu:~$ ls -l /mnt
total 32
[COLOR="Red"]drwxr-xr-x 106 1000 1000 16384 2009-01-09 21:57 di[/COLOR]
drwx------   2 root root 16384 2007-07-30 22:29 lost+found

```[/QUOTE]

---

### Post by caljohnsmith on 2009-01-17
You're right ajcham, my mistake, I didn't see that little "di" directory. :) Tubunu, how about doing:
```
nautilus /mnt/di &
```
And you should be able to access your home directory.

---

### Post by tubunu on 2009-01-17
Thanks. Well, I could access home dir anyway, it's on the 29GB partition. The code: *nautilus /mnt/di &* gives me the same function. Not sure I'm following..

---

### Post by caljohnsmith on 2009-01-17
OK, if you want to keep your home partition, that is going to take some more work, because as gparted has all ready warned you, you can't create any more primary partitions. How about we shrink your swap partition a little in order to make it possible for sdb4 to be a logical partition, and then convert your sdb4 partition into a logical partition. If that sounds OK with you, then first do:
```
sudo swapoff -a
sudo parted -s /dev/sdb resize 5 242437041s 243481076s
```
Then post the new output of:
```
sudo fdisk -lu /dev/sdb
sudo sfdisk -d /dev/sdb 
```
And we can go from there.

---

### Post by tubunu on 2009-01-17
```
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo parted -s /dev/sdb resize 5 242437041s 243481076s
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f9134d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    48805469    24402703+   7  HPFS/NTFS
/dev/sdb2        48805470   242436914    96815722+   7  HPFS/NTFS
/dev/sdb3       242436915   243481139      522112+   5  Extended
/dev/sdb4       243481140   300865319    28692090   83  Linux
/dev/sdb5       242437041   243481076      522018   82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdb
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 48805407, Id= 7, bootable
/dev/sdb2 : start= 48805470, size=193631445, Id= 7
/dev/sdb3 : start=242436915, size=  1044225, Id= 5
/dev/sdb4 : start=243481140, size= 57384180, Id=83
/dev/sdb5 : start=242437041, size=  1044036, Id=82

```

---

### Post by caljohnsmith on 2009-01-17
Looks like your swap partition was resized just fine, so how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk -f /dev/sdb -O ~/Desktop/sdb_sectors_modified.save < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output so I can check that everything went OK. Also, the above command will create a backup of the sectors being modified as a small "sdb_sectors_modified.save" file on your desktop, so that if for some reason anything were to go wrong, you can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. Next reboot your Live CD, and please post the new output of:
```
sudo fdisk -lu /dev/sdb
sudo sfdisk -d /dev/sdb
sudo parted /dev/sdb print
```
And we can go from there.

---

### Post by tubunu on 2009-01-17
```
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f9134d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    48805469    24402703+   7  HPFS/NTFS
/dev/sdb2        48805470   242436914    96815722+   7  HPFS/NTFS
/dev/sdb3       242436915   312576704    35069895    5  Extended
/dev/sdb5       242437041   243481076      522018   82  Linux swap / Solaris
/dev/sdb6       243481140   300865319    28692090   83  Linux

```
```

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdb
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 48805407, Id= 7, bootable
/dev/sdb2 : start= 48805470, size=193631445, Id= 7
/dev/sdb3 : start=242436915, size= 70139790, Id= 5
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=242437041, size=  1044036, Id=82
/dev/sdb6 : start=243481140, size= 57384180, Id=83

```
```

ubuntu@ubuntu:~$ sudo parted /dev/sdb print

Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  25.0GB  25.0GB  primary   ntfs         boot 
 2      25.0GB  124GB   99.1GB  primary   ntfs              
 3      124GB   160GB   35.9GB  extended                    
 5      124GB   125GB   535MB   logical   linux-swap        
 6      125GB   154GB   29.4GB  logical   ext3              

Information: Don't forget to update /etc/fstab, if necessary. 
```


EDIT: Hey, I can now create a new partition in GParted!!!!! :D Gee, I don't know how to thank you enough.

---

### Post by caljohnsmith on 2009-01-17
Looks like you should be all set; how about running gparted, and use that to create a logical partition with the unallocated space at the end of your drive. Let me know how that goes.

---

### Post by tubunu on 2009-01-17
Yup, created a logical partition and now I'm in the process of installing Ubuntu. Hoooorayyyyy!!! :D 

**[SIZE="7"]THANKYOUTHANKYOUTHANKYOU[/SIZE]**! :D 

You saved me from the hassle of burning all my valuable data to DVD's (that's a 160GB drive...), formatting everything and installing. I really appreciate all your effort. I'm sorry for taking up your time.

---

### Post by ajcham on 2009-01-17
Nice work caljohn! I can't tell you how much I learn just by lurking in your threads! :popcorn:
For that, I too thank you.

---

### Post by tubunu on 2009-01-17
For anyone having similar issues, I'm posting the final screenshot of the install wizard to show the end result of caljohnsmith's advice. Much respect. 

Now, excuse me, I'll disappear for a bit while I'm installing my Ubuntu! :popcorn:

---

### Post by caljohnsmith on 2009-01-17
You're welcome tubunu, glad it worked OK. Cheers and hope your new Ubuntu install goes smoothly. :)

[QUOTE=ajcham]Nice work caljohn! I can't tell you how much I learn just by lurking in your threads![/QUOTE]
Thanks for your kind words, ajcham, although we admittedly took the long way to get there; I misunderstood initially about what he was ultimately trying to accomplish. But at least we finally got to the point where he can reinstall now without losing his home partition. :)

---

