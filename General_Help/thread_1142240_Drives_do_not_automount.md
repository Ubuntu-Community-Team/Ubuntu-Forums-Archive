---
title: "Drives do not automount"
date: 2009-04-29
forum: General Help
---

### Post by Hagar55 on 2009-04-29
I installed ubuntu on my laptop(shiny new Dell Studio 17).
So far most of it is working like a charm (hibernate doesn't wake up correctly but I can do without that for now).

Trouble is there are two hard drives in the laptop, one is for the moment only the windows vista system drive, the other one is partitioned in the linux system (swap, root and home) and an ntfs partition.

Jaunty only mounts the linux partitions nothing else, while this isn't a problem to work it isn't convenient.

If you open the file browser and ask the properties of a mounted drive you can see mount the mount options and there is a line wich you can add properties. Is it possible to change the drive to automount without going into fstab ?
Is there a chance the system won't boot if you fill in something that isn't right ?

---

### Post by iaculallad on 2009-04-29
Could you post the output of the terminal command below:

```
sudo fdisk -l
```

---

### Post by Hagar55 on 2009-04-29
output from the terminal command :

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          22      176683+  de  Dell Utility
/dev/sda2              23        1328    10485760    7  HPFS/NTFS
/dev/sda3   *        1328       30402   233534464    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f702bec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18237   146487678+   7  HPFS/NTFS
/dev/sdb2           18238       19210     7815622+   5  Extended
/dev/sdb3           19211       22857    29294527+  83  Linux
/dev/sdb4           22858       30401    60597180   83  Linux
/dev/sdb5           18238       19210     7815591   82  Linux swap / Solaris

---

### Post by Nano_ext3 on 2009-04-29
What I do is first check, "sudo fdisk -l" to make I know which disk it is.  Then make sure you have the file systems, such as smbfs for samba and cifs, and another common one is ntfs-3g (which should be included).  Then I use the command "blkid" to get the UUID (unique ID) of that drive:

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AE846F33846EFCE9" TYPE="ntfs" 
/dev/sda2: UUID="0830EB9330EB8652" LABEL="Storage" TYPE="ntfs" 
/dev/sda3: UUID="bd6757f6-06a5-4c65-a6de-04b32a1d1ad7" TYPE="ext4" 
/dev/sda5: TYPE="swap" 

```

From here, I note which one is the one I want and insert that into fstab, IF its an internal drive, I don't put samba drives into fstab.  Make sure you create a folder in /mnt such as "sudo mkdir /mnt/MyDrive" as well.

For example, this is my windows drive:  

```
UUID=AE846F33846EFCE9	/mnt/Windows_Drive	ntfs-3g defaults 0 0 
```

Where, UUID is the UUID from the "blkid" command, and the folder Windows Drive that I created in /mnt, and its file system, ntfs-3g for NTFS and then defaults 0 0 is the safe to add on the end.  All of that structure is noted in the fstab file at the top.

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

UUID=AE846F33846EFCE9	/mnt/Windows_Drive	ntfs-3g defaults 0 0 
UUID=642148fe-c2f7-4b71-9b65-cb7a5f82e960 / ext4 defaults 0 1
UUID=f3253146-ce38-4cd0-ba00-5ad08873088e swap swap defaults 0 0
UUID=0830EB9330EB8652 /mnt/Storage ntfs-3g defaults 0 0 
 0
```

This helped fix my gf's computer, and I also hated have to click on the "automount" button of the drive under places to mount it.  This is way easier and a permanent solution, but you can always remove the entry in fstab later.

Cheers!

_Nano

---

### Post by Hagar55 on 2009-05-01
I installed ntfs-3g and now my datapartition automounts but the Vista OS partition still doesn't, so I guess now all I can do is go into fstab and change it manually ?

But with ntfs-3g there are now two fstab files, one is fstab, the other is fsab.pre-ntfs-config, in wich one should I make the changes ?

---

### Post by Nano_ext3 on 2009-05-01
The one you want to edit is "fstab" in /etc

I would not worry about the other one.  NTFS-3g , since 8.04 has been included I do believe.  Follow the same method of looking up its UUID with the command "blkid" then imputting it into fstab in the fashion I mentioned:

```

# <file system>        <dir>             <type>  <options> <dump> <pass>
UUID=AE846F33846EFCE9 /mnt/Windows_Drive ntfs-3g defaults    0      0 

```

You should only have to do this once, and make sure where you mount it (in my case /mnt/Windows_Drive), the directory is created there with "sudo mkdir /mnt/Window_Drive" or whatever you want to call it.  I use this to mount my vista drive.

Hope this helps, Note: spaces above don't matter as long as there is at least ONE space after each sectin such as "defaults 0 0"

Nano

---

### Post by Hagar55 on 2009-05-03
Ok I messed up, against better judgment and because I was to curious I tried altering the mounting settings of the OS partition with the "volume" tag of the drive properties. Clearly I made an error on the mounting setting because now the drive doesn't only not automount but I cannot mount it at all.

Problem is to acces the drive properties I have to mount it so I cannot undo it.

I get the following error:
Cannot mount volume.
Error org.freedesktop.Hal.Device.unknownError

Details
libhal.c1399: wrong reply from hald. Expexting an array.
org.freedesktop.Hal.Device.Volume.InvalidMountOption

So is there anyone who knows where I can undo the settings I altered ?

---

### Post by Nano_ext3 on 2009-05-03
You possibly could load a "Live CD" and access the hard drives files to undo the changes you made.

---

### Post by DeMus on 2009-05-03
> **Hagar55 said:**
> I installed ubuntu on my laptop(shiny new Dell Studio 17).
So far most of it is working like a charm (hibernate doesn't wake up correctly but I can do without that for now).

Trouble is there are two hard drives in the laptop, one is for the moment only the windows vista system drive, the other one is partitioned in the linux system (swap, root and home) and an ntfs partition.

Jaunty only mounts the linux partitions nothing else, while this isn't a problem to work it isn't convenient.

If you open the file browser and ask the properties of a mounted drive you can see mount the mount options and there is a line wich you can add properties. Is it possible to change the drive to automount without going into fstab ?
Is there a chance the system won't boot if you fill in something that isn't right ?

1) Unmount the mounted NTFS drive - right click on it on your desktop or in Nautilus en select unmount
2) In a terminal type:
```
sudo apt-get install ntfs-config
```
This will install the configuration manager for the NTFS drives
3) In menu System - Administration you find the NTFS Configuration tool. Click it, and in the small window you select the drives you want to mount, click OK. Now you make sure the thickbox with the text about the internal drives is ticked. Click OK again.
That's it. Also after a reboot the NTFS drives will be mounted.

---

### Post by BazookaAce on 2009-05-03
This works for me:

```
sudo apt-get install mountpy
```

```
sudo mountpy
```

---

### Post by Hagar55 on 2009-05-04
The trick with the ntfs-config tool worked this time round, last time it diden't feel like mounting the OS partition.

Thanks DeMus !

---

### Post by Hagar55 on 2009-05-04
Don't get me wrong I really like ubuntu, much more then I like Vista but there are way to many things that aren't documented and explained.

If there was a help file explaining what the tabs meant, what the different options where and how to use them I wouldn't have had all this trouble.

Same with filesharing over a home network, I'm just beginning to try and get that right. This should be something basic that's in the OS not something you have to install and go to terminal to get working !

These are still MAJOR things that need work for Ubuntu before it can start taking on Windows and Mac....

---

### Post by DeMus on 2009-05-04
> **Hagar55 said:**
> Don't get me wrong I really like ubuntu, much more then I like Vista but there are way to many things that aren't documented and explained.

If there was a help file explaining what the tabs meant, what the different options where and how to use them I wouldn't have had all this trouble.

Same with filesharing over a home network, I'm just beginning to try and get that right. This should be something basic that's in the OS not something you have to install and go to terminal to get working !

These are still MAJOR things that need work for Ubuntu before it can start taking on Windows and Mac....

You can't find anything here but it is a start:
[https://help.ubuntu.com/9.04/index.html]("https://help.ubuntu.com/9.04/index.html")

There are more sites with info, just google and I'm sure you find it.
Glad it worked. It's a way I have used several times and it always works for me.

---

### Post by Hagar55 on 2009-05-04
I've been there as well and it's usefull bit it's tiny compared to the help files a full OS should have....

---

### Post by DeMus on 2009-05-04
> **Hagar55 said:**
> I've been there as well and it's usefull bit it's tiny compared to the help files a full OS should have....

I know, I did write it is a start, didn't I? I do have 2 books about Linux and Ubuntu inwhich I can find a lot. They are called:
[LIST]
[*]Wiley - Ubuntu Linux Toolbox 1000 plus Commands for Ubuntu and Debian Power Users
[*]Wiley - Ubuntu Linux Bible Jan 2007
[/LIST]
Maybe if you can find those, you can learn more.

---

### Post by Hagar55 on 2009-05-05
I'll see if I can find them and if they're not to advanced for me (linux neewbie....).

But I still think the OS needs more documentation on it's own, and that's up to Canonical.

---

