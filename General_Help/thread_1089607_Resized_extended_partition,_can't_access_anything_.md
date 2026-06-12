---
title: "Resized extended partition, can't access anything other than linux partition"
date: 2009-03-07
forum: General Help
---

### Post by omaralqady on 2009-03-07
I was going to reinstall Windows XP but I needed a larger partition for it, so I used Gparted from the live cd to resize that partition. The thing is XP is on my primary partition, and then I had an extended partition that contains four logical ones, 2 for general use, one for swap, and one for ubuntu.

I decreased the size of the extended partition by reducing the size of the first logical partition in the extended partition, and then decreasing the extended partition and then increasing the primary partition to include the space I removed from the others, then I installed XP. When trying to boot GRUB didn't show, so I used the live cd to try to setup GRUB again but I couldn't so I used Super GRUB Boot Disk To Restore my GRUB.

Now everything is fine I can boot into Ubuntu or Windows XP, but Ubuntu can now only read it's own partition and one of the other three, and when I open Gparted it shows the whole disk as unallocated space not even displaying the Ubuntu partition:(.

----Sorry for the lengthy post, but I tried to include anything that could make the situation clearer :).

---

### Post by taurus on 2009-03-07
While in Ubuntu, open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by omaralqady on 2009-03-07
Here is the output for "sudo fdisk -l":
```
omar@3omar:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11511150

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+   c  W95 FAT32 (LBA)
/dev/sda2            2611        9729    57183367+   f  W95 Ext'd (LBA)
/dev/sda3            3826        6757    23551258+   b  W95 FAT32
/dev/sda5            2611        3825     9759424+   b  W95 FAT32
/dev/sda6            6758        6944     1502046   82  Linux swap / Solaris
/dev/sda7            6945        9729    22370481   83  Linux

```

for "sudo blkid":
```
omar@3omar:~$ sudo blkid
/dev/sda1: LABEL="SY$T3M" UUID="64A2-40C1" TYPE="vfat" 
/dev/sda5: LABEL="PROGS" UUID="49B0-3DBE" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="2ec856e1-68cb-422e-843f-e074c5fc3944" 
/dev/sda7: LABEL="Linux" UUID="32489dfa-bc46-4339-84ce-48378559795a" TYPE="ext3" 
/dev/sda8: LABEL="Linux" UUID="32489dfa-bc46-4339-84ce-48378559795a" TYPE="ext3" 
/dev/sda3: LABEL="F!L3$" UUID="0401-3605" TYPE="vfat" 

```

for "cat /etc/fstab":
```
omar@3omar:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=32489dfa-bc46-4339-84ce-48378559795a /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda8
UUID=2ec856e1-68cb-422e-843f-e074c5fc3944 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/sda1	/SYSTEM 	vfat	iocharset=utf8,umask=000	0	0
/dev/sda5	/PROGS		vfat	iocharset=utf8,umask=000	0	0
/dev/sda6	/FILES		vfat	iocharset=utf8,umask=000	0	0


```

for "df -h":
```
omar@3omar:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              21G   20G  105M 100% /
tmpfs                 473M     0  473M   0% /lib/init/rw
varrun                473M  344K  472M   1% /var/run
varlock               473M     0  473M   0% /var/lock
udev                  473M  2.7M  470M   1% /dev
tmpfs                 473M  444K  472M   1% /dev/shm
lrm                   473M  2.0M  471M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1              20G  4.3G   16G  22% /SYSTEM
/dev/sda5             9.3G  973M  8.4G  11% /PROGS
/dev/sda3              21G   20G  105M 100% /FILES
```

--I noticed a difference between fstab (refers to FILES as sda6) and df -h and blkid which refer to the same partition as sda3 ! and the weird thing is this is the only one that I can currently mount out of all of them !

---

### Post by taurus on 2009-03-07
> **omaralqady said:**
> Here is the output for "sudo fdisk -l":
```
omar@3omar:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11511150

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+   c  W95 FAT32 (LBA)
/dev/sda2            2611        9729    57183367+   f  W95 Ext'd (LBA)
/dev/sda3            3826        6757    23551258+   b  W95 FAT32
/dev/sda5            2611        3825     9759424+   b  W95 FAT32
/dev/sda6            6758        6944     1502046   82  Linux swap / Solaris
/dev/sda7            6945        9729    22370481   83  Linux

```

for "sudo blkid":
```
omar@3omar:~$ sudo blkid
/dev/sda1: LABEL="SY$T3M" UUID="64A2-40C1" TYPE="vfat" 
/dev/sda5: LABEL="PROGS" UUID="49B0-3DBE" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="2ec856e1-68cb-422e-843f-e074c5fc3944" 
/dev/sda7: LABEL="Linux" UUID="32489dfa-bc46-4339-84ce-48378559795a" TYPE="ext3" 
/dev/sda8: LABEL="Linux" UUID="32489dfa-bc46-4339-84ce-48378559795a" TYPE="ext3" 
/dev/sda3: LABEL="F!L3$" UUID="0401-3605" TYPE="vfat" 

```

for "cat /etc/fstab":
```
omar@3omar:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=32489dfa-bc46-4339-84ce-48378559795a /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda8
UUID=2ec856e1-68cb-422e-843f-e074c5fc3944 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/sda1	/SYSTEM 	vfat	iocharset=utf8,umask=000	0	0
/dev/sda5	/PROGS		vfat	iocharset=utf8,umask=000	0	0
/dev/sda6	/FILES		vfat	iocharset=utf8,umask=000	0	0


```

for "df -h":
```
omar@3omar:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              21G   20G  105M 100% /
tmpfs                 473M     0  473M   0% /lib/init/rw
varrun                473M  344K  472M   1% /var/run
varlock               473M     0  473M   0% /var/lock
udev                  473M  2.7M  470M   1% /dev
tmpfs                 473M  444K  472M   1% /dev/shm
lrm                   473M  2.0M  471M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1              20G  4.3G   16G  22% /SYSTEM
/dev/sda5             9.3G  973M  8.4G  11% /PROGS
/dev/sda3              21G   20G  105M 100% /FILES
```

--I noticed a difference between fstab (refers to FILES as sda6) and df -h and blkid which refer to the same partition as sda3 ! and the weird thing is this is the only one that I can currently mount out of all of them !

As you can see from the outputs, /dev/sda6 is your swap, not fat32 partition.  Therefore, you need to change the entry in /etc/fstab from

```
/dev/sda6	/FILES		vfat	iocharset=utf8,umask=000	0	0
```

to

```
UUID=0401-3605	/FILES		vfat	iocharset=utf8,umask=000	0	0
```
Save it and reboot.

Of course, you could replace the /dev/sda1 & /dev/sda5 with the UUID's in /etc/fstab.

---

### Post by omaralqady on 2009-03-07
Thanks a lot, this works :D. Although Gparted still reads the whole disk as unallocated space, any ideas on what I can do to fix this? :)

---

### Post by taurus on 2009-03-07
Post a screenshot of gparted.

---

### Post by omaralqady on 2009-03-07
Here is the screen shot of Gparted, and I tried to refresh it but still nothing changes.
[IMG]http://i43.tinypic.com/2n81uzp.png[/IMG]

---

### Post by hexanol on 2009-03-07
What's the ouput of "sudo parted /dev/sda unit s print" ? Is it also showing blank ?

---

### Post by omaralqady on 2009-03-07
Here is the output I received when I tried "sudo parted /dev/sda unit s print":

```
omar@3omar:~$ sudo parted /dev/sda unit s print
Error: Can't have overlapping partitions.
```

What does this mean? And how can I fix it??

---

### Post by hexanol on 2009-03-07
Well, you have a problem with the partition table in your MBR. Indeed, after looking a second time at your output of "fdisk -l":

```
/dev/sda1   *           1        2610    20964793+   c  W95 FAT32 (LBA)
/dev/sda2            2611        9729    57183367+   f  W95 Ext'd (LBA)
/dev/sda3            3826        6757    23551258+   b  W95 FAT32
/dev/sda5            2611        3825     9759424+   b  W95 FAT32
/dev/sda6            6758        6944     1502046   82  Linux swap / Solaris
/dev/sda7            6945        9729    22370481   83  Linux
```

You see /dev/sda3. It's right in the middle of your extended partition (i.e. in the middle of /dev/sda2). It looks like parted doesn't like this, and it may be quite normal, since the "non-official" specification of "DOS-type partition tables" says that "many systems assume that there is at most one primary partition with a type indicating an extended partition. Moreover, that its descriptor should describe a disk segment that contains all logical partitions and is disjoint from all other primary partitions. ". Here, we don't have the disjoint property, since the extended partition (/dev/sda2) goes from 2611-9729 but there's a primary partition (/dev/sda3) in 3826-6757. Even if this situation doesn't cause data corruption, some software may not like it.

There's way to repair this situation (i.e. make your /dev/sda3 partition a logical partition), but I only know the manual way, which is a bit time consuming and a bit dangerous. Basically, you need to edit manually the partitions tables with tools like "dd" and a hex editor.

---

### Post by omaralqady on 2009-03-07
Thanks a lot for your help, I'll try to do some research on that and try to do it and hopefully I won't destroy anything in the process :)

---

### Post by hexanol on 2009-03-07
If you still need some help, I could help you. I did something similar recently so I know what and where to make the corrections. Please note that, even if I know what I'm doing, I don't offer any guarantee! Basically, there's only 2 sectors you need to modify:

[LIST]
[*]Sector 0 (MBR)
[*]Sector X (first sector of /dev/sda5)
[/LIST]

If you give me the ouput of "sudo dd if=/dev/sda bs=512 count=1 | od -Ax -tx1" I will be able to help you further, if you want.

---

### Post by omaralqady on 2009-03-07
I definitely want and need your help :D Thanks a lot for sticking with me through this :)

here is the output you asked for:
```
omar@3omar:~$ sudo dd if=/dev/sda bs=512 count=1 | od -Ax -tx1
000000 eb 48 90 d0 bc 00 7c fb 50 07 50 1f fc be 1b 7c
000010 bf 1b 06 50 57 b9 e5 01 f3 a4 cb bd be 07 b1 04
000020 38 6e 00 7c 09 75 13 83 c5 10 e2 f4 cd 18 8b f5
000030 83 c6 10 49 74 19 38 2c 74 f6 a0 b5 07 b4 03 02
000040 ff 00 00 20 01 00 00 00 00 02 fa 90 90 f6 c2 80
000050 75 02 b2 80 ea 59 7c 00 00 31 c0 8e d8 8e d0 bc
000060 00 20 fb a0 40 7c 3c ff 74 02 88 c2 52 be 7f 7d
000070 e8 34 01 f6 c2 80 74 54 b4 41 bb aa 55 cd 13 5a
000080 52 72 49 81 fb 55 aa 75 43 a0 41 7c 84 c0 75 05
000090 83 e1 01 74 37 66 8b 4c 10 be 05 7c c6 44 ff 01
0000a0 66 8b 1e 44 7c c7 04 10 00 c7 44 02 01 00 66 89
0000b0 5c 08 c7 44 06 00 70 66 31 c0 89 44 04 66 89 44
0000c0 0c b4 42 cd 13 72 05 bb 00 70 eb 7d b4 08 cd 13
0000d0 73 0a f6 c2 80 0f 84 ea 00 e9 8d 00 be 05 7c c6
0000e0 44 ff 00 66 31 c0 88 f0 40 66 89 44 04 31 d2 88
0000f0 ca c1 e2 02 88 e8 88 f4 40 89 44 08 31 c0 88 d0
000100 c0 e8 02 66 89 04 66 a1 44 7c 66 31 d2 66 f7 34
000110 88 54 0a 66 31 d2 66 f7 74 04 88 54 0b 89 44 0c
000120 3b 44 08 7d 3c 8a 54 0d c0 e2 06 8a 4c 0a fe c1
000130 08 d1 8a 6c 0c 5a 8a 74 0b bb 00 70 8e c3 31 db
000140 b8 01 02 cd 13 72 2a 8c c3 8e 06 48 7c 60 1e b9
000150 00 01 8e db 31 f6 31 ff fc f3 a5 1f 61 ff 26 42
000160 7c be 85 7d e8 40 00 eb 0e be 8a 7d e8 38 00 eb
000170 06 be 94 7d e8 30 00 be 99 7d e8 2a 00 eb fe 47
000180 52 55 42 20 00 47 65 6f 6d 00 48 61 72 64 20 44
000190 69 73 6b 00 52 65 61 64 00 20 45 72 72 6f 72 00
0001a0 bb 01 00 b4 0e cd 10 ac 3c 00 75 f4 c3 00 00 00
0001b0 00 00 00 00 00 00 00 00 50 11 51 11 00 00 80 01
0001c0 01 00 0c fe ff ff 3f 00 00 00 73 cb 7f 02 00 fe
0001d0 ff ff 0f fe ff ff b2 cb 7f 02 0f 19 d1 06 00 fe
0001e0 ff ff 0b fe ff ff f0 a1 a9 03 35 ba ce 02 00 00
0001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa
000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00334233 s, 153 kB/s
```

---

### Post by hexanol on 2009-03-07
Actually I forgot that I'll need at least one free sector if I want to put back your primary partition into the linked-list of logical partition, so right now it's uncertain if it will or not work...

Give me the output of "sudo dd if=/dev/sda bs=512 count=1 skip=41929650 | od -Ax -tx1"

---

### Post by omaralqady on 2009-03-07
Here it is:
```
omar@3omar:~$ sudo dd if=/dev/sda bs=512 count=1 skip=41929650 | od -Ax -tx1
000000 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
*
0001b0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
0001c0 ff ff 05 fe ff ff 01 00 00 00 fe d5 29 01 00 00
0001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
*
0001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa
000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000600356 s, 853 kB/s
```

-I think I had 8 MBs that I couldn't add to any partition when I was resizing, are the sectors int that space free sectors?

---

### Post by hexanol on 2009-03-07
I don't like what I see... there is suposed to be 2 partition descriptors in the last output you gave me and there's only one of type 05... anyway, give me the output of "sudo dd if=/dev/sda bs=512 count=1 skip=41929651 | od -Ax -tx1"

> I think I had 8 MBs that I couldn't add to any partition when I was resizing, are the sectors int that space free sectors?
Yes, but I need those sectors to be at a specific place, and that's what we should find out soon.

---

### Post by omaralqady on 2009-03-07
Here is the output:
```

omar@3omar:~$ sudo dd if=/dev/sda bs=512 count=1 skip=41929651 | od -Ax -tx1
000000 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
*
0001b0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
0001c0 ff ff 0b fe ff ff 7d 00 00 00 81 d5 29 01 00 fe
0001d0 ff ff 05 fe ff ff 73 90 f8 03 fb d6 2d 00 00 00
0001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa
000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0024911 s, 206 kB/s
```

-I think those 8 MB's where exactly before or after /dev/sda1(the only primary partition) but I can't remember if it's exactly before or exactly after.

---

### Post by hexanol on 2009-03-07
> **omaralqady said:**
> 
-I think those 8 MB's where exactly before or after /dev/sda1(the only primary partition) but I can't remember if it's exactly before or exactly after.

Right now you have 3 primary partition to be exact (trust me :)). And from the number I have right now, there's no 8MB before or after the first partition.

Here's a good (but a bit technical) source of information about "DOS-type partition tables" [http://www.win.tue.nl/~aeb/partitions/partition_tables.html](http://www.win.tue.nl/~aeb/partitions/partition_tables.html) .

EDIT: I'm out for a while (1 or 2 hours). I'll continue to work on your problem after, I might need more information. I guess it's getting pretty late in Egypt, isn't ;) ?

---

### Post by omaralqady on 2009-03-07
LOL, yes it is, it's 1:00 AM now and I was just debating whether to keep doing this or just go to sleep because I have to go to college tomorrow :D
But since after you get back it'll be about 3:00 AM I guess I'd better go to sleep then and I hope we'll continue this tomorrow. And once again thanks for your time and effort :)
So I'll talk to you tomorrow.:D

---

### Post by hexanol on 2009-03-07
Well, news are good. Should be able to fix this by the end of the day.

First, backup the sectors of your drive that we will soon rewrite. Those are sectors 0, 41929651 and 61448625. If something goes wrong (miscalculated something, etc, the risk is real since the work I have done is error prone, and it's not like I have done this all my life) then you'll be able to restore your disk like it was before. You should also backup your ordinary files so if something goes really wrong (bad manipulation, like mistyping a command) then you'll still have your files. Note that what we are going to do is a risky manipulation, but it should goes well. Do it at your own risk!

So, backup your sectors. This is how it's done
```
$ sudo dd if=/dev/sda of=s0.backup bs=512 count=1
$ sudo dd if=/dev/sda of=s41929651.backup skip=41929651 bs=512 count=1
$ sudo dd if=/dev/sda of=s61448625.backup skip=61448625 bs=512 count=1
```

This will create 3 512-bytes files. Save them somewhere safe (on a USB stick, on another computer, on some computer on the internet, etc). We'll only need them if something is wrong.

For now, I need your MBR in a binary form before altering it. Give me the result of "sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | base64".

Give me also the result of "sudo dd if=/dev/sda bs=512 count=1 skip=108551206 | od -Ax -tx1". I don't really need it, but it's only to be sure.

---

### Post by omaralqady on 2009-03-08
Here is the output of "sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | base64":

```
omar@3omar:~$ sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | base64
60iQ0LwAfPtQB1Af/L4bfL8bBlBXueUB86TLvb4HsQQ4bgB8CXUTg8UQ4vTNGIv1g8YQSXQZOCx0
9qC1B7QDAv8AACABAAAAAAL6kJD2woB1ArKA6ll8AAAxwI7YjtC8ACD7oEB8PP90AojCUr5/feg0
AfbCgHRUtEG7qlXNE1pSckmB+1WqdUOgQXyEwHUFg+EBdDdmi0wQvgV8xkT/AWaLHkR8xwQQAMdE
AgEAZolcCMdEBgBwZjHAiUQEZolEDLRCzRNyBbsAcOt9tAjNE3MK9sKAD4TqAOmNAL4FfMZE/wBm
McCI8EBmiUQEMdKIysHiAojoiPRAiUQIMcCI0MDoAmaJBGahRHxmMdJm9zSIVApmMdJm93QEiFQL
iUQMO0QIfTyKVA3A4gaKTAr+wQjRimwMWop0C7sAcI7DMdu4AQLNE3IqjMOOBkh8YB65AAGO2zH2
Mf/886UfYf8mQny+hX3oQADrDr6Kfeg4AOsGvpR96DAAvpl96CoA6/5HUlVCIABHZW9tAEhhcmQg
RGlzawBSZWFkACBFcnJvcgC7AQC0Ds0QrDwAdfTDAAAAAAAAAAAAAABQEVERAACAAQEADP7//z8A
AABzy38CAP7//w/+//+yy38CDxnRBgD+//8L/v//8KGpAzW6zgIAAAAAAAAAAAAAAAAAAAAAVao=
```

And for "sudo dd if=/dev/sda bs=512 count=1 skip=108551206 | od -Ax -tx1":

```
omar@3omar:~$ sudo dd if=/dev/sda bs=512 count=1 skip=108551206 | od -Ax -tx1
000000 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
*
000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.012334 s, 41.5 kB/s
```

---

### Post by hexanol on 2009-03-08
Ok, results are in!

First, you'll need to boot from a LiveCD. What we'll do will modify the partition order and I'm not sure if it's safe to do this from your Ubuntu installation. Indeed, after our modifications, we'll have
[LIST]
[*]/dev/sda3 -> /dev/sda6
[*]/dev/sda6 -> /dev/sda7
[*]/dev/sda7 -> /dev/sda8
[/LIST]
So, to be on the safe side, boot from a LiveCD, and don't mount any of your partitions (or at least unmount them before doing the "destructive part" - more on this later)

You'll have to create the 3 new sectors. This is how it's done (things in bold are instructions)
```
$ base64 -d > s0.new
60iQ0LwAfPtQB1Af/L4bfL8bBlBXueUB86TLvb4HsQQ4bgB8CXUTg8UQ4vTNGIv1g8YQSXQZOCx0
9qC1B7QDAv8AACABAAAAAAL6kJD2woB1ArKA6ll8AAAxwI7YjtC8ACD7oEB8PP90AojCUr5/feg0
AfbCgHRUtEG7qlXNE1pSckmB+1WqdUOgQXyEwHUFg+EBdDdmi0wQvgV8xkT/AWaLHkR8xwQQAMdE
AgEAZolcCMdEBgBwZjHAiUQEZolEDLRCzRNyBbsAcOt9tAjNE3MK9sKAD4TqAOmNAL4FfMZE/wBm
McCI8EBmiUQEMdKIysHiAojoiPRAiUQIMcCI0MDoAmaJBGahRHxmMdJm9zSIVApmMdJm93QEiFQL
iUQMO0QIfTyKVA3A4gaKTAr+wQjRimwMWop0C7sAcI7DMdu4AQLNE3IqjMOOBkh8YB65AAGO2zH2
Mf/886UfYf8mQny+hX3oQADrDr6Kfeg4AOsGvpR96DAAvpl96CoA6/5HUlVCIABHZW9tAEhhcmQg
RGlzawBSZWFkACBFcnJvcgC7AQC0Ds0QrDwAdfTDAAAAAAAAAAAAAABQEVERAACAAQEADP7//z8A
AABzy38CAP7//w/+//+yy38CDxnRBgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVao=
**(Hit Ctrl+D)**

$ base64 -d > s41929651.new
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/v//C/7//30A
AACB1SkBAP7//wX+////1SkBdLrOAgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVao=
**(Hit Ctrl+D)**

$ base64 -d > s61448625.new
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/v//C/7//z8A
AAA1us4CAP7//wX+//9zkPgD+9YtAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVao=
**(Hit Ctrl+D)**

```

This will create 3 new files. Just to be sure that everything is intact, enter "md5sum s0.new s41929651.new s61448625.new". You should get exactly this output
```
$ md5sum s0.new s41929651.new s61448625.new 
653faa5c1a2261dbe2543717810b22fc  s0.new
2ac29bb50dc59fa5436f1e4df8b9fa46  s41929651.new
72add7a75e3724af6ce2973f46e78d7d  s61448625.new

```
If you get something different, don't continue this procedure.

Ok, here's the destructive part! This is where we'll write the new sectors. This is as simple as entering these 3 commands
```
$ sudo dd if=s0.new of=/dev/sda bs=512 count=1 seek=0
$ sudo dd if=s41929651.new of=/dev/sda bs=512 count=1 seek=41929651
$ sudo dd if=s61448625.new of=/dev/sda bs=512 count=1 seek=61448625
```

After each commands, you should always get a message similar to this
```
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.0228e-05 s, 25.3 MB/s

```

Now that we have rewritten the sectors, launch gparted and enjoy/cry. :D

If gparted still show blank, you can restore your original sectors (those you saved in my last post) with these commands
```
$ sudo dd if=s0.backup of=/dev/sda bs=512 count=1 seek=0
$ sudo dd if=s41929651.backup of=/dev/sda bs=512 count=1 seek=41929651
$ sudo dd if=s61448625.backup of=/dev/sda bs=512 count=1 seek=61448625
```

---

### Post by omaralqady on 2009-03-08
Thanks a lot, I'll try this and let you know the results :)
But I'll have to do it tomorrow :S since I don't have anything to backup the old sectors on.
I'll post back here when I'm with good results hopefully :D

---

### Post by hexanol on 2009-03-08
Well, for the sectors, do you have a web-mail (hotmail, gmail, etc) account for example ? You could "tar" those 3 files and send them to your own email address. This is relatively safe.

But like I said in my other post, I also suggest you to backup your "precious" files. Disaster should not happen but I can't guarantee 100%, and it might be better to play it safe.

---

### Post by omaralqady on 2009-03-08
-I am getting a new external hard disk tomorrow so I'll backup everything I have on it and give it a shot.

-I can't use email because for some reason I have never been able to access the internet when using live cd.

--What's the worst thing that could happen if something goes wrong??
Will I just have to do a complete format or something worse??

---

### Post by hexanol on 2009-03-08
The worst thing would be overwriting a sector we didn't backup because of an error in the command I gave you (or a mistype) -- but they looks fine. Overwriting a sector at random could give something between a corrupt file or a damaged file-system. Thus the worst that can happens is losing data. Data could be unrecoverable but the hard disk will always be.

Also, I forgot to tell you that you might have to modify slightly your menu.lst file to be able to reboot in Linux once you'll have done the manipulation. I could tell you if you post the output of "cat /boot/grub/menu.lst".

---

### Post by omaralqady on 2009-03-08
Thanks, I was afraid I might lose the disk itself, this makes it much easier for me :D So if you can please post what I've to do with menu.lst, and once I back everything up tomorrow and go through with the process, I'll post the results back. :) Thanks for everything :D

---

### Post by hexanol on 2009-03-08
Well, post the output of "cat /boot/grub/menu.lst" and I'll tell you what to do, if there's something to do.

And your welcome! I just hope that everything is going to be fine for you!

---

### Post by omaralqady on 2009-03-08
Here is my menu.lst:

```
omar@3omar:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.22-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=32489dfa-bc46-4339-84ce-48378559795a ro  single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

-It has three kernels with their recovery and the memtest and an entry for Win XP but I plan on reinstalling it after I'm done with the sector editing, but I don't know if that matters.

---

### Post by hexanol on 2009-03-08
You'll only need to replace every occurrence of (hd0,7) to (hd0,8 ). Don't do this before making the manipulations, and even if you forget to make them, it doesn't matter much since you can always edit manually the entry from the grub menu.

---

### Post by omaralqady on 2009-03-08
That's the easiest thing till now :D but you said in the post to change from (hd0,7) to (hd0,??), I only see a smiley in that place :)


-Never mind, I saw in the email that it's (hd0,"8") :)

---

### Post by omaralqady on 2009-03-09
Everything worked perfectly :D

Thank you very very much for your time and effort and for sparing me having to reformat and reinstall everything from scratch :)

---

### Post by hexanol on 2009-03-09
Well I'm glad to hear this! And you're welcome.

Could you just post the output of "sudo parted /dev/sda unit s print" ? This will be my reward. ;)

---

### Post by hallbrian on 2009-03-10
Hi, i have been following this post, and i am glad to hear that all is well and everthing is working..


@hexanol nice work buddy.

---

### Post by omaralqady on 2009-03-10
Hi,
I'm sorry to tell you this, but after reinstalling XP for three times in one week I was too frustrated to even think about reinstalling it again so I let a friend of mine do it, and he accidentally deleted all partitions(if that's possible!! but he also said he thought that was what I wanted so I think he's just covering up himself !!) when setting it up so I had to set up everything again from scratch :S but at least I had backed up my data :S but your work was lost. But it did work absolutely perfect if that's of any comfort for you :), I could see the partitions in Gparted, even edit them again if I wanted to, it was perfect :D.

-I'm sorry for replying so late but you can see I had my hands full with reinstalling Ubuntu again and my files, and if it's of any help, when I found out what he did I broke the windows cd in half ;) :D

--But even though your work was lost, my gratitude isn't, so if I can ever help you with anything( although that's not likely :) )just let me know . :)

---

### Post by hexanol on 2009-03-10
Hehe, that's a funny story. Shame on your friend for destroying my "handmade" sectors! :P

But there's no problem with this. It was fun actually, although it took me a bit more time than I thought (especially to write the messages since english is not my "first" language, I have to be careful if I want my sentences to be comprehensible).

@hallbrian thanks for the comment!

---

### Post by omaralqady on 2009-03-10
LOL, Maybe it sounds funny now, but it wasn't so funny then :D

And don't worry your English is very comprehensible :)

---

