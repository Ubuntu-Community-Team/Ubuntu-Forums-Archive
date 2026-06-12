---
title: "mounting NTFS and FAT32 drives on startup"
date: 2005-08-17
forum: Desktop Environments
---

### Post by uperjer on 2005-08-17
i know that the /etc/fstab file has to be amended to do this, but i'm not sure exactly what to put in it.  

this is my drive information:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2040    16386268+   7  HPFS/NTFS
/dev/hda2            2041        4865    22691812+  83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       15988   128423578+   7  HPFS/NTFS
/dev/hdb2           15989       19457    27864742+   c  W95 FAT32 (LBA)


i'd really like to mount hda1, hdb1, and hdb2 on startup.  any help would be greatly appreciated.

---

### Post by h4rdc0d3 on 2005-08-17
:) The FAT32 partition is easy because both Linux and Windows both can read and write it by default.

Try adding this to your /etc/fstab:
```
/dev/hdb2 	 /media/fat 	vfat	rw,auto,user 	 0	 0
```
Of course, then you'll need to do:
 ```
mkdir /media/fat
mount -a
``` 

](*,) For your NTFS partitions, you'll going to have to at least use a kernel mod and I can't help you with that. Anyone else?

---

### Post by crispingatiesa on 2005-08-17
This should be enough:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by uperjer on 2005-08-17
[QUOTE=crispingatiesa]This should be enough:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)[/QUOTE]

i tried using that, but for some reason all of my drives (except the linux partition) came up as the fat32 drive.  i really don't know what i'm doing wrong.

---

### Post by crispingatiesa on 2005-08-17
post your fstab here

---

### Post by uperjer on 2005-08-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb2 	 /media/fat 	vfat	rw,auto,user 	 0	 0


i got the fat32 parition taken care of no problem.  it's the ntfs drives i can't get mounted for some reason.

---

### Post by Buffalo Soldier on 2005-08-17
[QUOTE=uperjer]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb2 	 /media/fat 	vfat	rw,auto,user 	 0	 0


i got the fat32 parition taken care of no problem.  it's the ntfs drives i can't get mounted for some reason.[/QUOTE]
 i can't see any ntfs entry in your fstab.

what's the output when you do **sudo fdisk -l** at the terminal?

---

### Post by crispingatiesa on 2005-08-17
sudo mkdir /media/windows

sudo mount /dev/hdb1 /media /windows/ -t ntfs -o umask=0222

if it works  add

/dev/hdb1       /media/windows  ntfs    umask=0222      0       0

to the fstab

if it doesn't work then we need to check if the NTFS library is loaded (I believe that kernel 2.6 and older have the NTFS library in it)

So do:

modprobe -l ntfs  (is an L not an i)

If it shows somethng like this /lib/modules/2.6.10-5-k7/kernel/fs/ntfs/ntfs.ko
 then the module is loaded  and  I dont have a clue of what is going on

I think that kernels is higher or equal than 2.6  should have th elibraries in them 

If it doesn't get the library,  go to Synaptic and search NTFS and install the libraries (I think is  libntfs5)

good luck

---

### Post by Buffalo Soldier on 2005-08-17
I'm assuming these are the NTFS partitions that you would like to mount:[QUOTE=uperjer]/dev/hda1   *           1        2040    16386268+   7  HPFS/NTFS
/dev/hdb1   *           1       15988   128423578+   7  HPFS/NTFS[/QUOTE]

I think this is the steps that you should do.[list=1]
[*] Create Local mount folder **/media/windows1** and **/media/windows2**.
```
sudo mkdir /media/windows1
sudo mkdir /media/windows2
```

[*] Backup your fstab file.
```
sudo cp /etc/fstab /etc/fstab_backup
```

[*] Open your fstab file.
```
sudo gedit /etc/fstab
```

[*] Add these entries into your fstab:
```
proc		/proc		proc		defaults			0	0[color=red]
/dev/hda1       /media/windows1	ntfs		nls=utf8,umask=0222		0	0
/dev/hdb1       /media/windows2	ntfs		nls=utf8,umask=0222		0	0[/color]
/dev/hda2	/ 		ext3		defaults,errors=remount-ro	0	1
/dev/hdd	/media/cdrom0	udf,iso9660	ro,user,noauto			0	0
/dev/hdc	/media/cdrom1	udf,iso9660	ro,user,noauto			0	0
/dev/fd0	/media/floppy0	auto			rw,user,noauto			0	0
/dev/hdb2	/media/fat		vfat			rw,auto,user				0	0
```
[/list]

p/s: Sorry for not reading your earlier post. You already post your **fdisk -l**. My bad and sorry for using gedit, just substitute the word gedit with what KDE default text editor is.

---

### Post by uperjer on 2005-08-18
[QUOTE=Buffalo Soldier]I'm assuming these are the NTFS partitions that you would like to mount:

I think this is the steps that you should do.[list=1]
[*] Create Local mount folder **/media/windows1** and **/media/windows2**.
```
sudo mkdir /media/windows1
sudo mkdir /media/windows2
```

[*] Backup your fstab file.
```
sudo cp /etc/fstab /etc/fstab_backup
```

[*] Open your fstab file.
```
sudo gedit /etc/fstab
```

[*] Add these entries into your fstab:
```
proc		/proc		proc		defaults			0	0[color=red]
/dev/hda1       /media/windows1	ntfs		nls=utf8,umask=0222		0	0
/dev/hdb1       /media/windows2	ntfs		nls=utf8,umask=0222		0	0[/color]
/dev/hda2	/ 		ext3		defaults,errors=remount-ro	0	1
/dev/hdd	/media/cdrom0	udf,iso9660	ro,user,noauto			0	0
/dev/hdc	/media/cdrom1	udf,iso9660	ro,user,noauto			0	0
/dev/fd0	/media/floppy0	auto			rw,user,noauto			0	0
/dev/hdb2	/media/fat		vfat			rw,auto,user				0	0
```
[/list]

p/s: Sorry for not reading your earlier post. You already post your **fdisk -l**. My bad and sorry for using gedit, just substitute the word gedit with what KDE default text editor is.[/QUOTE]


this worked PERFECTLY.  thank you SO MUCH for your help!

---

