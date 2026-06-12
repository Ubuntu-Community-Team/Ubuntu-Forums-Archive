---
title: "I Am New To Linux and Have A Few Questions"
date: 2005-11-26
forum: Desktop Environments
---

### Post by bigmikeherrmann on 2005-11-26
I am currently using Ubuntu 5.10 and am having some trouble. i was running SLAX kill Bill editon and it was very easy to get to my hard drive with all my music, videos, and picutres but i am having some trouble finding out how to get to my hardrive. Can someone help me

---

### Post by Specialsauce on 2005-11-26
[QUOTE=bigmikeherrmann]I am currently using Ubuntu 5.10 and am having some trouble. i was running SLAX kill Bill editon and it was very easy to get to my hard drive with all my music, videos, and picutres but i am having some trouble finding out how to get to my hardrive. Can someone help me[/QUOTE]
im ot exactly understanding the problem.....

---

### Post by bigmikeherrmann on 2005-11-26
My problem is that i cant find my harddrive with all my files on it. i am in the Filesystem folder and cannot figure out how to get to my harddrive

---

### Post by Remmelas on 2005-11-26
Can you provide a short description of what files you are trying to find?  The 'filesystem' folder IS your hard drive.  most of the files you would normally save and work with (ie not your operating system files) are going to be found in the /home/username directory, and other drives/partitions besides your system drive would likely be under /media

---

### Post by bigmikeherrmann on 2005-11-26
i was runing windows and i had a folder for all my downloads which is where i kept all my music and it was

C:\Program Files\Bitlord\Downloads

and i am trying to find that folder so i can have all my music
and i am trying to find My Document which is where ii also kept my music

---

### Post by dsjas297 on 2005-11-26
If you have multiple partitions and hard drives, and you chose to set the partitioning yourself, you could have easily not set some partitions or hard drives to mount in Ubuntu.

---

### Post by Barnaby on 2005-11-26
Hi there, I hope not but you could also easily have deleted your windows partition. Do you have multiple harddrives or partitions? You sure Win is still there?

Usually all your drives are under the /mount directory , incl. cd, floppy, pen drives etc. Take a look there might be your C drive listed, but it's not gonna be called C.

Barnaby

---

### Post by oldmanstan on 2005-11-26
Ok, try this in a terminal window...

```
sudo mkdir /mnt/windows
sudo mount /dev/hda1 /mnt/windows
```

this assumes that your linux partition is hda0 and windows is on the hda1 partition (this is the way ubuntu will generally set it up by default, at least in my experience).

mkdir creates a folder under /mnt (just a convenient place in linux to mount stuff) where the contents of your windows drive will go

mount actually "mounts" the windows drive there so it can be accessed

if this doesn't work try fiddling with the hda1 part... without knowing where windows is on your system it's impossible to help further

---

### Post by Kokanee on 2005-11-26
Okey.  Lets see whats on you hard drive.  Open your terminal and type...

```
sudo fdisk -l
``` 
Enter you password when prompted. Then cut and paste the output into a post here so we can see whats in your computer and go from there.

---

### Post by bigmikeherrmann on 2005-11-26
I Still cannot access my hardrive i clicked system admisistration then discs and in there i saw

Hard Disc
74.76gb

which is my hard drive but i click it and it dosent do anything
also when i click the Partitions tab it says under device

/dev/hda1 

so i went there and clicked it and again i got nothing

---

### Post by bigmikeherrmann on 2005-11-26
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@your-i0mmef9hzg:~$


thats what i got when i did what Kokanee said to do im not sure what it means

---

### Post by byourg on 2005-11-26
In disk manager, partitions, how many patitions are listed for your hard drive? You are looking for one that has a FAT32 or NTFS filesystem. Look in the access path box and if it is empty click the change button to create a mount point for it. After that the browse button should be enabled so you can browse the files and get to your music files.

---

### Post by bigmikeherrmann on 2005-11-26
Well under partion list it says

Partition 1

---

### Post by byourg on 2005-11-26
In disks manager, If you only have one hard disk in the left pane, and in the partitions tab you only have one partition with a extended 3 partition, you wiped out the windows partition. Sorry!

---

### Post by bigmikeherrmann on 2005-11-26
I Do have 3 hard discs in the left pane

---

### Post by Neobuntu on 2005-11-26
Whoa now. It's my understanding that ubuntu does NOT enable access to other drive and partition by default in order to protect them. You may not want all user accessing you Windows or Media partitions or drives.

It's easy.

System > Administration > Disks

Find your disk or partition and click enable.

As a good security practice this will need to be done after each reboot. You can of course make it permanent but be careful.

---

### Post by Zwack on 2005-11-26
O.K. Let's start with the simple stuff.  

Open a terminal and type the following...

```
cat /var/log/dmesg|grep hd
```

you should get something like this

```
:~$ cat /var/log/dmesg | grep "hd"
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[   13.530971]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:pio
[   13.530985]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:pio
[B][   13.794666] hda: ST340014A, ATA DISK drive
[   15.078011] hdc: LITE-ON CD-RW SOHR-5238S, ATAPI CD/DVD-ROM drive[/B]
[   17.741113] hda: max request size: 1024KiB
[   17.741665] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   17.741790] hda: cache flushes supported
[   17.784904] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[   26.231102] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
[   26.540292] EXT3 FS on hda1, internal journal
:~$
```

You're looking for lines like the bold ones...
These tell us I have a Seagate ST340014A as hda and a LITE-ON CD-RW as hdc...

In this case we are interested in the hda drive... you might have more than one hard drive installed, so make a note of the names of all of them.

then try 
```
sudo fdisk -l /dev/hda
```

You will be prompted for your password, and then you will get the information we need.

Something like this.
```
:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    5  Extended
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris
:~$
```

This tells us that we have two partitions on this disk  
/dev/hda1 is a Linux partition
/dev/hda2 is an extended partition
and /dev/hda5 is a swap partition inside the extended partition.

Repeat this for every disk that you find and post the results here.  We can then give you the exact command you will need to mount the windows partition if it still exists.

I hope that this helps,

Z.

---

