---
title: "NTFS Partition Problem"
date: 2009-01-28
forum: General Help
---

### Post by acid1114 on 2009-01-28
A friend of mine has just moved from Windows XP to Ubuntu 8.10. But he says, that he can't open his NTFS partition. So his question is, how can he open his NTFS partition or atleast can he convert it to ext3 for his Ubuntu.

---

### Post by Sam Lars on 2009-01-28
Ubuntu should be able to read NTFS, is he getting an error or is it not showing up?

---

### Post by acid1114 on 2009-01-28
He says he gets an error.

---

### Post by acid1114 on 2009-01-28
Here's the error that he gets: 

Cannot mount volume.
Unable to mount the volume "160GB"

---

### Post by ubhi on 2009-01-28
what type of error he faced...
can u explain..

ubuntu automatically mount the ntfs partition..
if its not done...
then you can do that manually by using mount at terminal

open the terminal from Application -> accer-> terminal

mkdir /media/paritionname  (give name of your partition0
mount /dev/sda1 /media/partionname ntfs-3g

try once if it succeed then make entry in /etc/fstab
to make it permanent mount

---

### Post by GepettoBR on 2009-01-28
We need more information to help you.

Is Windows still installed on the NTFS partition? If so, it has to stay as NTFS.

Ubuntu can read NTFS partitions without the need to install any extra packages at least since Gutsy. What version is he using?

Maybe he doesn't have read access to the partition. please ask him for the contents of his /etc/fstab file and post it here.

Finally, if he does want to format it to ext3 he can do it with Partition Editor (package name "gparted") but formatting will erase all data on the partition, so he should make sure he has a backup of everything he wants to keep.

---

### Post by Sam Lars on 2009-01-28
Before we get too crazy, there is a known bug that causes an error to pop up when mounting a volume.  It is actually mounted correctly despite the error, so you can close the error and then access it normally.

---

### Post by acid1114 on 2009-01-28
Said that he never had Windows on that partition, as he kept it for a storage device (for photos, docs..) and also he doesn't have Windows on his PC now, only Ubuntu. 
He is using version 8.10, downloaded from Ubuntu's website. And here is the content of his /etc/fstab file - 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=abd781ca-15cf-47e5-901e-053c08b607fc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=32db5adf-ce08-4829-afd0-63e0139cba3e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I know about gparted and already told him, but he says that he can't format his partition (he doesn't have a backup).

---

### Post by GepettoBR on 2009-01-28
There's a problem, the drive isn't even listed in fstab. We'll have to add one. Ask him to run "sudo fdisk -l" in a terminal and post the results.

---

### Post by acid1114 on 2009-01-28
Here : 

bgph@bgph-desktop:~$  sudo fdisk -l
[sudo] password for bgph: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda79bebe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19456   156280288+   7  HPFS/NTFS

---

### Post by GepettoBR on 2009-01-28
Alright, have your friend try to mount the drive as root. If it works, we can edit fstab to make it permanent. The following command will mount the drive in /media/data:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/data
```
if it doesn't work, try removing "-3g" from after "ntfs" and running it again.

---

### Post by acid1114 on 2009-01-28
Well here's what happened. I gave him the command, he wrote (copied) it in the terminal and here are the results:

bgph@bgph-desktop:~$  sudo mount -t ntfs-3g /dev/sdb1 /media/data
[sudo] password for bgph: 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/data -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/data ntfs-3g force 0 0

Since he doesn't have Windows he thought that the right Choice is number 2 so he wrote the command - sudo  mount -t ntfs-3g /dev/sdb1 /media/data -o force

The results:

bgph@bgph-desktop:~$ sudo  mount -t ntfs-3g /dev/sdb1 /media/data -o force
[sudo] password for bgph: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.


fuse: failed to access mountpoint /media/data: No such file or directory

Anyway, he says that now he can access his partition. He can copy, cut, delete ... so his partition is fully working now ;). Is it permanent now or does it need something else?

---

### Post by GepettoBR on 2009-01-28
> **acid1114 said:**
> Well here's what happened. I gave him the command, he wrote (copied) it in the terminal and here are the results:

bgph@bgph-desktop:~$  sudo mount -t ntfs-3g /dev/sdb1 /media/data
[sudo] password for bgph: 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/data -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/data ntfs-3g force 0 0

Since he doesn't have Windows he thought that the right Choice is number 2 so he wrote the command - sudo  mount -t ntfs-3g /dev/sdb1 /media/data -o force

The results:

bgph@bgph-desktop:~$ sudo  mount -t ntfs-3g /dev/sdb1 /media/data -o force
[sudo] password for bgph: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.


fuse: failed to access mountpoint /media/data: No such file or directory

Anyway, he says that now he can access his partition. He can copy, cut, delete ... so his partition is fully working now ;). Is it permanent now or does it need something else?

Yay, good for him! :) :) Two things:

Fist, why it wasn't working. The last Windows shutdown wasn't clean, which means the filesystem in that disk wasn't cleanly unmounted. That's why it wasn't being accessed. "force" changed that, so it should work from now on.

Second, since the partition was not accessable, an entry for it wasn't written in fstab, which lists the filesystems to be automatically mounted at boot. To make the change permanent (in other words, to make it mount automatically), /etc/fstab must be edited, and a line added for that filesystem. This must be done as root, so we should also back up the original file just in case:```
sudo cp /etc/fstab /etc/fstab.backup && gksudo gedit /etc/fstab
```

Now, add the following two lines:```
#/dev/sdb1
[color=red]UUID[/color] [color=blue]/media/data[/color] ntfs-3g defaults,umask=007,gid=46 0       1
```

[color=red]The UUID is a long string of characters that is unique for each partition. To discover what value to put here, open another terminal and run ```
blkid
```This will display the UUID of every partition in the computer. Copy and paste the UUID for /dev/sdb1 onto the beginning of the line, WITH the preceding UUID= and WITHOUT the quotation marks (for example, UUID=c91da0c7-8339-4279-8a0a-5086e71ae7d7)[/color]

[color=blue]/media/data was an arbitrary location I chose to test the mount, but the drive can be mounted anywhere. The location you select here will be the mount point. Make sure it exists, though. If, for example you want to mount the drive as /storage, you need to create the directory with ```
sudo mkdir /storage
``` (if you want to mount inside your own home directory, the word "sudo" should not be used before the mkdir command)[/color]

Make sure that you haven't made any typos, or else it won't work. Use the other entries in fstab as reference if you fear you're doing something wrong. There aren't any spaces after the commas in the part that says "defaults,umask=007,gid=46", that is intentional. If you want to restore the backup, just type ```
sudo cp /etc/fstab.backup /etc/fstab
``` to get the original file back. To test if the change worked, restart the computer and try to access the drive.


EDIT: I know you said this was your friend's problem, but its easier to write instructions in second person. I hope that's not a problem.

---

### Post by bpl07 on 2009-01-28
> sudo apt-get install ntfs-config

This program configures your ntfs drive(s) to be automounted everytime.  Once installed, it's accessible from System > Administration > NTFS Configuration Tool

---

### Post by GepettoBR on 2009-01-28
> **bpl07 said:**
> This program configures your ntfs drive(s) to be automounted everytime.  Once installed, it's accessible from System > Administration > NTFS Configuration Tool

Wow, how nifty! Indeed it updated my fstab upon use. acid1114, this is safer than editing fstab directly. One correction, though. On my system the menu entry was in Applications>System Tools, not System>Administration.

If the problem is solved, please don't forget to mark the thread as SOLVED to help others who might have the same problem.

---

