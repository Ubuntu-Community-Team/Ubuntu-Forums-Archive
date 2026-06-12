---
title: "Share Permission &amp; Auto mount issues"
date: 2009-03-17
forum: General Help
---

### Post by mpcsm on 2009-03-17
Hi I'm new to Ubuntu so please excuse my lack of knowledge.

I have 2 issues and hope you can help me with these.

Issue 1: I have a drive that I'd like to have it mount automatically on startup. How do I do that?

Issue 2: There is a folder in that same drive called "My Document". I set it as a shared folder (right mouse button and select "Sharing Option" I checked the "Share this folder" and "Allow other people to write in this folder"). 
 
When I reboot Ubuntu and restart the system, the "Share this folder" option is retained as checked, but the "Allow other people to write in this folder" is not retained.
How do I retain "Allow other people to write in this folder" on restart?

---

### Post by iaculallad on 2009-03-17
> **mpcsm said:**
> 
Issue 1: I have a drive that I'd like to have it mount automatically on startup. How do I do that?

Try adding the drive/partition in your /etc/fstab file which as previously discussed in this [thread]("http://ubuntuforums.org/showthread.php?t=1098456").

> **mpcsm said:**
> 
Issue 2: There is a folder in that same drive called "My Document". I set it as a shared folder (right mouse button and select "Sharing Option" I checked the "Share this folder" and "Allow other people to write in this folder"). 
 
When I reboot Ubuntu and restart the system, the "Share this folder" option is retained as checked, but the "Allow other people to write in this folder" is not retained.
How do I retain "Allow other people to write in this folder" on restart?

Set the folder permission:

```
sudo chmod -R 777 /mount_point/My\ Document
```

*Above command is just a sample, change it to fit your setting*

---

### Post by mpcsm on 2009-03-17
Now I really stuffed thing up.

I tried to change fstab but couldn't get the parameters to work.
Here is what I put in.

/dev/sda2 /media/data vfat user,auto,exec,rw
That resulted in an error message telling me that /media/data could not be mounted.

I commented the line in fstab and things were back the way they were.

Now I though by right click on the drive that I mounted, I selected the property of the drive, and there I found the "mount options" parameters in one of the tabs.
I entered "user,auto,exec" no quotes and now I can not access the drive no matter what I do.

Sorry I did say I'm a newbie.
Are you able to help me
1. Get the drive to be mounted again.
2. Tell me what I did wrong in my fstab parameters?

Thanks

---

### Post by taurus on 2009-03-17
Instead of using that entry for your /dev/sda2 in /etc/fstab, try this one.

```

/dev/sda2   /media/data   vfat   iocharset=utf8,umask=000  0  0
```
Save it and mount your /dev/sda2, assuming you already have that mount point, /dev/data.

```
sudo mount -a
df -h
```

Everyone should be able to write to /media/data now.

---

### Post by mpcsm on 2009-03-17
Hi taurus
Because i've changed the "mount options" parameters in one of the drive property tabs and entered "user,auto,exec" no quotes, I can not access the drive no matter what I do.

I can see the drive in "Computer" but I can not see the "mount options" tab any more.
It seams that the bad parameters I put in the "mount options" cannot be changed through the GUI.

When I tried your code
/dev/sda2   /media/data   vfat   iocharset=utf8,umask=000  0  0
I still can not mount the drive.

Code 
sudo mount -a

Result:
[mntent]: line 9 in /etc/fstab is bad
mount: mount point /media/data does not exist

Code
df -h result in
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              49G  8.5G   38G  19% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  300K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile

---

### Post by taurus on 2009-03-17
Post these.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
ls -la /media
```

---

### Post by mpcsm on 2009-03-17
**sudo fdisk -l**

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6e6fa46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6632    53271508+   7  HPFS/NTFS
/dev/sda2           13541       38913   203808622+   b  W95 FAT32
/dev/sda3            6633       13015    51271447+  83  Linux
/dev/sda4           13016       13540     4217062+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         969     1953439+   6  FAT16



**sudo blkid**
/dev/sda1: UUID="B2D82AFFD82AC209" TYPE="ntfs" 
/dev/sda2: UUID="48CE-B3AA" TYPE="vfat" 
/dev/sda3: UUID="26593fdd-f70e-4fcb-bbcc-a3e16bf25fe6" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="1c89e281-4a9b-4f2d-92f1-25f52a5bdf84" 
/dev/sdc1: SEC_TYPE="msdos" UUID="1020-FE20" TYPE="vfat" 



 **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=26593fdd-f70e-4fcb-bbcc-a3e16bf25fe6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=1c89e281-4a9b-4f2d-92f1-25f52a5bdf84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


**ls -la /media**
total 48
drwxr-xr-x  4 root    root  4096 2009-03-18 09:39 .
drwxr-xr-x 20 root    root  4096 2009-03-14 00:45 ..
lrwxrwxrwx  1 root    root     6 2009-03-13 23:59 cdrom -> cdrom0
drwxr-xr-x  2 root    root  4096 2009-03-13 23:59 cdrom0
drwx------  3 michael root 16384 1970-01-01 10:00 disk
-rw-r--r--  1 root    root   110 2009-03-18 09:39 .hal-mtab
-rw-------  1 root    root     0 2009-03-18 09:39 .hal-mtab-lock

---

### Post by taurus on 2009-03-17
Edit /etc/fstab and add this line back to the end of it.

```
/dev/sda2   /media/data   vfat   iocharset=utf8,umask=000  0  0
```
Now, you need to create that new mount point before you can mount it.

```
sudo mkdir /media/data
sudo mount -a
df -h
```

---

### Post by mpcsm on 2009-03-17
I can now see the drive and it is automatically mounted when I restart the system. Thanks.

However, I'm not able to 
1. Unmount the drive
2. Share it or any of the folders within it, as it is controlled by root.

How do I change the permission to be able to unmount and share the drive and its contents.

Thanks again

---

### Post by taurus on 2009-03-17
If you want to unmount it, just run

```
sudo umount /dev/sda2
-or-
sudo umount /media/data
```

What do you mean by sharing it?  You should be able to write to /media/data anytime you want even if root is the owner.

```
ls -la /media/data
```

---

### Post by mpcsm on 2009-03-17
Hi taurus
I'd like to be able to mount and unmount the drive (via the GUI) without Sudo

Re sharing: I'd like to make the drive a shared drive for access to through the network.
Before this issue came up, I was able to right click on the drive, and tick "Share this folder" and "Allow other people to write in this folder" 

Now I get "net usershare returned error 255: net usershare add: cannot share path /media/data/my documents as we are restricted to only sharing directories we own. Ask the administrator to add the line "usershare owner only = false" to the global section of smb.conf to allow this.

Sorry for the silly questions and hope you don't mind helping...Much appreciated.

---

### Post by mpcsm on 2009-03-18
Found the answer.

Added the following OPTIONS to fstab
users,auto,rw

Seams to work OK :) 

Thanks for all your help

---

