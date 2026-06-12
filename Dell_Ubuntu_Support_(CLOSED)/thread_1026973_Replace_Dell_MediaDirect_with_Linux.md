---
title: "Replace Dell MediaDirect with Linux"
date: 2008-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LegoAddict on 2008-12-31
I am running a Dell Inspiron 1525 that was given to me with Windows Vista but I have since carved up as follows to run Intrepid x64 (in order):



40 MB FAT16 - No idea what this is.  I think Windows needed it.
9.8 GB NTFS - Win Vista Recovery
152.6 GB NTFS - Windows VistaOS

6.24 MB UNALLOCATED (this is junk left over from Vista's partitioner)

Under an extended partition:

7.45 GB LINUX SWAP (for ubuntu)
18.63 GB EXT3 - Ubuntu / partition
46.57 GB EXT3 - Ubuntu /home partition
60.53 GB UNALLOCATED - This was mine.  I downsized Vista as much as it would let me and I left this open as an option
2.5 GB FAT32 - Dell MediaDirect


The Dell Media Direct is what I take issue with.  Ever since I installed Ubuntu it started bluescreening and I don't really want it.  However, I want the shiny button to start it on my laptop...

My question was if it would be possible to reformat that partition for DMD and install on it XBMC Live (Hardy based) or some other Linux-based media center.  The Inspiron 1525 has run Ubuntu without issue (simple wireless driver was the only hangup and I just needed to hook it up with a compatible adapter) and so I would really, REALLY like to ditch DMD.

All I want to do is press the little house button on my laptop and have XBMC Live or some other Linux open.

---

### Post by damis648 on 2008-12-31
Install the distro of your choice onto that partition (Ubuntu?), but set it so that grub installs on the partition, NOT the whole drive (in the Ubuntu installed it is on the very has page before install, if you are not using Ubuntu for this write back). Then when it is done reboot (grub and your MBR should be unchanged) and boot Windows. In Windows, pop in your MediaDirect CD that came with your laptop and then start cmd AS ADMINISTRATOR (A MUST!) and issue the following
```
X:\dellkit\rmbr.exe DELL Y Z
```
replacing X with the drive letter for the CD, as well as replacing Y for the partition to boot with the power button (your default Ubuntu install) and Z with the new install's partition number (partition to boot with MediaDirect)

---

### Post by LegoAddict on 2008-12-31
Just so I'm clear:

Create a partition (perhaps add to the DMD with some of the unallocated) and install XBMC Live.

Then use my DMD CD and open Vista, run the given command with the letters Windows gives to the drives as stated, and voi'la?

---

### Post by damis648 on 2009-01-01
> **LegoAddict said:**
> Just so I'm clear:

Create a partition (perhaps add to the DMD with some of the unallocated) and install XBMC Live.

Then use my DMD CD and open Vista, run the given command with the letters Windows gives to the drives as stated, and voi'la?

Pretty much, but when installing XBMC Live you have to make sure to install grub to the partition and not the MBR. If the installer doesn't have that option, you will need to do it manually. Post back if you do. Also, the command
```
X:\dellkit\rmbr.exe DELL Y Z
```
that I posted will end up looking like this
```
X:\dellkit\rmbr.exe DELL 2 4
```
or something like that, notice they are partition numbers.

---

### Post by damis648 on 2009-01-01
Double post.:-\

---

### Post by LegoAddict on 2009-01-01
I don't quite understand this part about GRUB vs MBR.  I know MBR is the Windows-based one but wouldn't it just be added as an entry under Ubuntu's GRUB?

---

### Post by llamakc on 2009-01-01
I'm interested in the results of this also. I have the same setup and would love to utilize the DMD partition this way.

---

### Post by armandh on 2009-01-01
Master boot record [mbr] is where the bios looks in the HDD for an OS. it may find GRand Unified Bootloader [grub] and offer selections from there or it may find Lilo or the windows equivalent. it may only find direction to an OS chain loader.


What ever is in the mbr can include choices resident on other partitions or drives. there is only one active mbr per drive but the other drives may be switched in by having CD, usb or floppy in a drive and a priority in the bios. or in some bios by swapping master slave or primary / secondary IDE lines

clear as mud 
YMMV depending on hardware/bios

---

### Post by LegoAddict on 2009-01-01
Sorry, all I heard was a whooshing sound as that explanation rushed past me :confused:

What exactly will I have to do?

---

### Post by armandh on 2009-01-01
I have never been successful getting the windows boot loader to offer OS other than microsoft products. here the help of those who have succeeded is invited. while grub seems to offer all available OS. the last install is the one that counts as to modifying the MBR that the bios is currently choosing.

I was stuck for days trying a triple boot that could not be done because of the way two of the OS loaded.

first read books on this stuff, understand, experiment. 
[not on mission critical equipment]

---

