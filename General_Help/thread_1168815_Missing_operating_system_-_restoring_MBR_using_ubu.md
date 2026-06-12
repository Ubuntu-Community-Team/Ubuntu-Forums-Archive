---
title: "Missing operating system - restoring MBR using ubuntu"
date: 2009-05-24
forum: General Help
---

### Post by Fanas on 2009-05-24
I've got a problem, I was using Windows 7 system and some screw up later it tells "missing operating system" whenever I try to load. I guess it is my MBR problems. I'd use windows recovery tool, but currently I have physical access only to my ubuntu 8.10 live cd.
So I ask to help me restore my OS using ubuntu. :)

---

### Post by Super TWiT on 2009-05-24
I actually have a text file with instructions I have saved just for this event.  Open up a terminal on the livecd.  Then, try these commands ```
sudo grub
find /boot/grub/stage1
root (hd?,?)
```
(replace ? marks with hd numbers from step 2)
```
setup (hd0)
quit
```

---

### Post by Fanas on 2009-05-24
> **Super TWiT said:**
> I actually have a text file with instructions I have saved just for this event.  Open up a terminal on the livecd.  Then, try these commands ```
sudo grub
find /boot/grub/stage1
root (hd?,?)
```
(replace ? marks with hd numbers from step 2)
```
setup (hd0)
quit
```

find /boot/grub/stage1
returns
Error 15: File not found

---

### Post by Super TWiT on 2009-05-24
Oh, did you not have linux installed on this machine?  Hmm... In that case try ```
sudo grub-install hd0
```

---

### Post by Fanas on 2009-05-24
> **Super TWiT said:**
> Oh, did you not have linux installed on this machine?  Hmm... In that case try ```
sudo grub-install hd0
```

It returns:
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by lindsay7 on 2009-05-24
If the problem is with a broken mbr you can try this form the live cd

Type in the terminal "sudo apt-get install lilo" then "sudo lilo -M /dev/sda mbr" , this will reset your windows mbr and boot windows. sda is the same as hd0.

---

### Post by kiridude on 2009-05-24
using your live cd, open a terminal and post the output of:

```
fdisk -l
```

This way we can get a better idea of what's going on.

---

### Post by Fanas on 2009-05-24
> **kiridude said:**
> using your live cd, open a terminal and post the output of:

```
fdisk -l
```

This way we can get a better idea of what's going on.

It returns:
Cannot open /dev/sda

---

### Post by kiridude on 2009-05-24
sorry 

```
sudo fdisk -l
```

---

### Post by Fanas on 2009-05-24
> **kiridude said:**
> sorry 

```
sudo fdisk -l
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32682   262518133+  83  Linux
/dev/sda2           32683       32695      103803+  17  Hidden HPFS/NTFS
/dev/sda3           32695       37781    40854698+  17  Hidden HPFS/NTFS
/dev/sda4           37782       38913     9092790    f  W95 Ext'd (LBA)
/dev/sda5           37782       38913     9092758+  82  Linux swap / Solaris

---

### Post by Fanas on 2009-05-24
> **lindsay7 said:**
> If the problem is with a broken mbr you can try this form the live cd

Type in the terminal "sudo apt-get install lilo" then "sudo lilo -M /dev/sda mbr" , this will reset your windows mbr and boot windows. sda is the same as hd0.

It now returns:
No boot signature in partition

---

### Post by kiridude on 2009-05-24
Ok, try the following:

```
sudo grub
root (hd0,0)
setup (hd0)
```

before the directions given by supertwit

EDIT: you must choose if you want lilo bootloader or grub. Don't try to use both. I did not see the last post.

---

### Post by Fanas on 2009-05-24
> **kiridude said:**
> Ok, try the following:

```
sudo grub
root (hd0,0)
setup (hd0)
```

before the directions given by supertwit
After setup (hd0)

Error 17: Cannot mount selected partition

---

### Post by Fanas on 2009-05-24
P.S. Before all those commands I could mount windows partition, now I cant.

---

### Post by kiridude on 2009-05-24
It looks like you may have a filesystem problem, so unmount everything and in a terminal with the live CD run:

```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` 

then try it again.

---

### Post by Fanas on 2009-05-25
> **kiridude said:**
> It looks like you may have a filesystem problem, so unmount everything and in a terminal with the live CD run:

```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` 

then try it again.

e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



I can't do anything, probably my partitions gone to dust.
Will probably need to format whole hard disk, I just wish I could save a few files, which I need critically.

---

### Post by unutbu on 2009-05-25
There are other recovery techniques you could try in order to recover those files, but they would require that you have at least roughly 270GB of free hard drive space. 
These techniques require a fair amount of time and patience.

Here you will find information on a number of recovery tools: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Here are two possibilities:
[list]
[*] First you use partimage to clone sda1 to a new partition. (Here is where you would need the extra 270GB of free hard drive space). Then you run 
```

sudo dumpe2fs /dev/sda1 |  awk /superblock/{'print $4'}
```

to find a list of superblocks on sda1.
The superblocks are like FAT (file allocation tables) -- they describe where all your files on sda1 are located. Your primary superblock is not working. That is what the error message "e2fsck: Bad magic number in super-block while trying to open /dev/sda1" is telling us. So we can try one of the backup superblocks with 
```

sudo e2fsck -b XXXXX -fy /dev/sda1
```

where XXXXX needs to be replaced with the superblock number found from the "dumpe2fs" command above.

[*]Or, you could boot the LiveCD, install the testdisk package, and run
```

sudo photorec
```

Photorec will ask you where to save any files it finds. Here you again need about 270 GB of extra hard disk space. Photorec will then search sda1 byte-by-byte looking for chunks of data that it recognizes as .jpeg, or .doc, or whatever. It can recognize a large number of formats. The problem is, it will not be able to recover the whole file if the file is fragmented -- i.e. not residing in a contiguous block of hard drive space. So the whole process is a bit hit-or-miss.
[/list]

If you would like to try either of these techniques, I can try to help you through it.

---

### Post by Fanas on 2009-05-25
> **unutbu said:**
> There are other recovery techniques you could try in order to recover those files, but they would require that you have at least roughly 270GB of free hard drive space. 
These techniques require a fair amount of time and patience.

Here you will find information on a number of recovery tools: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Here are two possibilities:
[list]
[*] First you use partimage to clone sda1 to a new partition. (Here is where you would need the extra 270GB of free hard drive space). Then you run 
```

sudo dumpe2fs /dev/sda1 |  awk /superblock/{'print $4'}
```

to find a list of superblocks on sda1.
The superblocks are like FAT (file allocation tables) -- they describe where all your files on sda1 are located. Your primary superblock is not working. That is what the error message "e2fsck: Bad magic number in super-block while trying to open /dev/sda1" is telling us. So we can try one of the backup superblocks with 
```

sudo e2fsck -b XXXXX -fy /dev/sda1
```

where XXXXX needs to be replaced with the superblock number found from the "dumpe2fs" command above.

[*]Or, you could boot the LiveCD, install the testdisk package, and run
```

sudo photorec
```

Photorec will ask you where to save any files it finds. Here you again need about 270 GB of extra hard disk space. Photorec will then search sda1 byte-by-byte looking for chunks of data that it recognizes as .jpeg, or .doc, or whatever. It can recognize a large number of formats. The problem is, it will not be able to recover the whole file if the file is fragmented -- i.e. not residing in a contiguous block of hard drive space. So the whole process is a bit hit-or-miss.
[/list]

If you would like to try either of these techniques, I can try to help you through it.

I just need to recover a few megabites. All the movies and music I can download easily again.
It would really suck, to get my RSS feeds again for example.
So I'd need to recover firefox bookmarks.
Also I've got a few documents I need to recover.
And a few save files for a game.

---

### Post by unutbu on 2009-05-25
I understand, but unfortunately, the second recovery technique (using photorec) does not work that way.

The first suggestion, using dumpe2fs followed by e2fsck, can be done without cloning sda1 first. However, e2fsck may alter your filesystem in an irreversible way. 

Cloning sda1 and working from the cloned partition is safest because it affords you the opportunity to try many recovery techniques. Without cloning first, you may worsen your situation.

---

### Post by Fanas on 2009-05-25
> **unutbu said:**
> I understand, but unfortunately, the second recovery technique (using photorec) does not work that way.

The first suggestion, using dumpe2fs followed by e2fsck, can be done without cloning sda1 first. However, e2fsck may alter your filesystem in an irreversible way. 

Cloning sda1 and working from the cloned partition is safest because it affords you the opportunity to try many recovery techniques. Without cloning first, you may worsen your situation.

Unfortunately I do not have as much free space. So I guess I'll have to risk.

---

