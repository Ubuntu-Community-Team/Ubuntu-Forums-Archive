---
title: "Raid not recognised"
date: 2008-12-14
forum: General Help
---

### Post by lift_test on 2008-12-14
Have just done a clean install of Ibex.  Previous installs have always treated the 2 raid disks as individual disks.  During the install it recognised the raid disks.  However they are still shown as 2 separate disks but if you try to access either it comes up with the error  "can't mount volume".
If I run GParted each disk appears twice:

/dev/mapper/pdc_ebhhcgjhi  (111.76GiB)
/dev/mapper/pdc_ebhhcgihi5 (111.74GiB)
/dev/sda                   (111.79GiB)
/dev/sdb                   (111.79GiB)

The first entry shows 7.84MiB as unallocated at the beginning, second entry is all allocated.  Third and fourth entries show 7.84MiB at front and 31.38MiB at end of disks.

From the first 2 entries I assume that some attempt has been made to map them as raid but not succeeded and renderered them inaccesible.

I don't need to write to these disks in Ubuntu but it would make life easier if I could read them

They still work OK as raid in XP

---

### Post by GoofusGreen on 2008-12-14
Hey,

I've recently put together a new desktop. It's got Vista 64-bit on a 500-gig RAID setup. I was going to install Intrepid on it also, I noticed that the RAID drives show up as 2 separate unallocated 250-gig drives. 

I have a third hard disk, a single 500-gig ntfs drive. This shows up just fine. If I install Intrepid on the 500-gig non-raid drive, will GRUB still work properly? Also, how will I be able to mount the RAID drives in Ubuntu?

-Goofus

---

### Post by fjgaude on 2008-12-15
To see the raid drives created in BIOS for Windows you need to install a program called **dmraid**. After that read the man pages for it and then you will be able to load the raid in Ubuntu.

Use Synaptic to install dmraid from the repository. This article helps:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Good luck!

---

### Post by lift_test on 2009-01-01
Thanks for the info, have been away on holiday and just started catching up.  The dmraid is installed so I tried removing completely (via Synaptic) and rebooting.  This once again showed the raid correctly as 2 Sata drives.  I could also mount and read them, which is exactly what is required.  Out of curiosity I reinstalled dmraid, rebooted and couldn't mount the drives!  So the problem seems to be dmraid itself or incompatibility with the asus motherboard (PS48X).

---

### Post by fjgaude on 2009-01-01
Well, from what little I know, a BIOS raid array is not something you can install Linux on. Program **dmraid** is used to mount such an array but you need to have booted Ubuntu from a separate drive then use dmraid to mount the raid array.

---

### Post by lift_test on 2009-01-01
Linux is installed on the (Windows) C: drive disk but obviously on another partition.  I was just trying to access the 2 Sata discs because that is where I keep all my data files on the raid 5 array.  If dmraid is not loaded I can access the files on each disk (because both disks are identical) but both are umountable if dmraid is loaded.

---

### Post by fjgaude on 2009-01-01
The array is raid5? with two disks?

AFAIK, only very late issues of dmraid can recognize raid5.

Show us what **df -h** looks like, please.

---

### Post by lift_test on 2009-01-02
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              28G  3.0G   24G  12% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  328K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  3.0M  756M   1% /dev
tmpfs                 759M  592K  758M   1% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc6             125G  1.1G  118G   1% /home
/dev/sdh1              15G   11G  4.7G  70% /media/disk
/dev/sdg1              16M 1008K   15M   7% /media/disk-1
/dev/sdd1             244M   35M  210M  15% /media/TOSHIBA256M

Must have got confused with raid Nos, it's 2 disks showing as 1 so that each disk is identical.  Confusingly neither disk shows up in df -h but if I go Places/Computer both show up as SATA and can be mounted(dmraid not loaded).  Each disk is an WDC SATA of 111.7 GB.
Correction, after mounting they show as follows:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              28G  3.0G   24G  12% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  328K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  3.0M  756M   1% /dev
tmpfs                 759M  592K  758M   1% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc6             125G  1.1G  118G   1% /home
/dev/sdg1              16M 1008K   15M   7% /media/disk-1
/dev/sdd1             244M   35M  210M  15% /media/TOSHIBA256M
/dev/sda5             112G   46G   67G  41% /media/SATA
/dev/sdb5             112G   46G   67G  41% /media/SATA_

As I said before, I only really want to access the RAID to read files.  If I want to change or save anything for Windows I use another disk in case it corrupts anything by writing to only 1 disk.  However it would be nice to use the array under Ubuntu as I do in Windows.
Thanks for your help.

---

### Post by fjgaude on 2009-01-02
> **GoofusGreen said:**
> Hey,

I've recently put together a new desktop. It's got Vista 64-bit on a 500-gig RAID setup. I was going to install Intrepid on it also, I noticed that the RAID drives show up as 2 separate unallocated 250-gig drives. 

I have a third hard disk, a single 500-gig ntfs drive. This shows up just fine. If I install Intrepid on the 500-gig non-raid drive, will GRUB still work properly? Also, how will I be able to mount the RAID drives in Ubuntu?

-Goofus

Okay, you now! If you install Ubuntu on the single 500G drive you will be able to boot either into Windows or into Linux. You have to have a partition for Ubuntu on that drive. The liveCD install disk shows what has to be done pretty clearly. After install as you boot you will get a grub menu that permits continuing the boot into either Windows or Ubuntu.

Happy computing.

---

### Post by fjgaude on 2009-01-02
> **lift_test said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              28G  3.0G   24G  12% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  328K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  3.0M  756M   1% /dev
tmpfs                 759M  592K  758M   1% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc6             125G  1.1G  118G   1% /home
/dev/sdh1              15G   11G  4.7G  70% /media/disk
/dev/sdg1              16M 1008K   15M   7% /media/disk-1
/dev/sdd1             244M   35M  210M  15% /media/TOSHIBA256M

Must have got confused with raid Nos, it's 2 disks showing as 1 so that each disk is identical.  Confusingly neither disk shows up in df -h but if I go Places/Computer both show up as SATA and can be mounted(dmraid not loaded).  Each disk is an WDC SATA of 111.7 GB.
Correction, after mounting they show as follows:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              28G  3.0G   24G  12% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  328K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  3.0M  756M   1% /dev
tmpfs                 759M  592K  758M   1% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc6             125G  1.1G  118G   1% /home
/dev/sdg1              16M 1008K   15M   7% /media/disk-1
/dev/sdd1             244M   35M  210M  15% /media/TOSHIBA256M
/dev/sda5             112G   46G   67G  41% /media/SATA
/dev/sdb5             112G   46G   67G  41% /media/SATA_

As I said before, I only really want to access the RAID to read files.  If I want to change or save anything for Windows I use another disk in case it corrupts anything by writing to only 1 disk.  However it would be nice to use the array under Ubuntu as I do in Windows.
Thanks for your help.

Okay, you are booting into Ubuntu on /dev/sdc2. You can now use **dmraid** to mount the BIOS raid1, mirror, array.

If you don't have dmraid on your system, you can get it like so:

```
sudo apt-get install dmraid
```

After than try reading the man pages for it:

```
man dmraid
```

to get an idea how it is used.

Start with this:

```
sudo dmraid -ay
```

which will show what you have.

The you will make a mountpoint for the array, like so:

```
sudo mkdir /raid
```

You could create any mountpoint, as you wish, e.g., /home/raid. Then you will mount using something like this:

```
sudo mount -t ntfs /dev/mapper/pdc_ebhhcgjhi /raid
```

If it doesn't work at first try different values of the pdc_ item. Notice what the **dmraid -ay** showed and use that.

After you have gotten through this all okay, then we can show you how to have all the mounting done on bootup by placing a line in **/etc/fstab** file.

---

### Post by lift_test on 2009-01-03
Tried that, result below, seems as though it doesn't recognise as valid ntfs volume

vic@assus:~$ sudo dmraid -ay
[sudo] password for vic: 
RAID set "pdc_ebhhcgjhi" already active
RAID set "pdc_ebhhcgjhi5" already active
vic@assus:~$ sudo mkdir /raid
vic@assus:~$ sudo mount -t ntfs /dev/mapper/pdc_ebhhcgjhi /raid
NTFS signature is missing.
Failed to mount '/dev/mapper/pdc_ebhhcgjhi': Invalid argument
The device '/dev/mapper/pdc_ebhhcgjhi' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
vic@assus:~$  sudo mount -t ntfs /dev/mapper/pdc_ebhhcgjhi5
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

I'm afraid it's a bit beyond me!

---

### Post by fjgaude on 2009-01-03
Did not this work:

```
vic@assus:~$ sudo mount -t ntfs /dev/mapper/pdc_ebhhcgjhi5 /raid
```

I know the one with the trailing t didn't.

When you created the array in your BIOS you did use NTFS as the file type, eh?

---

### Post by lift_test on 2009-01-11
Still won't mount if dmraid is loaded.  If it's not loaded I can mount 1 or both.

---

