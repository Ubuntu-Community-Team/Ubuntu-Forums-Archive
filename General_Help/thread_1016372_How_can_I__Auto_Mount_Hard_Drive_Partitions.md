---
title: "How can I  Auto Mount Hard Drive Partitions?"
date: 2008-12-19
forum: General Help
---

### Post by tarvinder on 2008-12-19
Hello,
Prior to switching to Xubuntu, I was using PCLOS2007, where everything was basically GUI based and easy and worked well. After trying out Ubuntu,I installed Xubuntu,since it is a PIII system with 256 MB ram and I wanted my OS to run faster, so I chose Xubuntu. I have a 320GB HDD as primary and it is Single boot with Xubuntu on sda1. Then there is separate partition for my music files on this drive which is sda6. Secondary Hard Drive is 500GB which is sdb1, on which I store my movie files. I am able to mount sda6 and sdb1 manually via terminal. However I want them to mount automatically everytime at boot. When go to edit my fstab file, I think there is some problem, since i can't see sdb1 and sda6 values make no sense. I'm posting both fdisk -l and fstab values. Please help me to correct the fstab file based on fdisk values.

First fdisk -l
----------
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0135eea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1019     8185086   83  Linux
/dev/sda2            1020       38914   304386075+   5  Extended
/dev/sda5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sda6            1529       38914   300297532+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux
---------------------------

Now the fstab values

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5c3aa897-a2f0-48c1-8bf4-d691d6a4f83e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=116c6ab8-2436-44c3-a90f-b99c08c7b966 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

----------

Please help me to auto mount my sda6 and sb1. Thank You in advance.

---

### Post by DamonChyld on 2008-12-19
Here is my cheat sheet for my NAS, same principle though ;)

```
sudo gedit /root/.credentials
	username=###
	password=### 
sudo chmod 600 /root/.credentials
cd /
sudo mkdir bigdisk *(Personal pref where you want to put this, I dont like putting in in mnt or media cause I dont like having desktop icons)*
sudo gedit /etc/fstab 
//192.168.0.2/bigdisk /bigdisk cifs credentials=/root/.credentials,rw,auto,uid=<user ID>,gid=<user ID>
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
sudo mount -a (or restart)

```

---

### Post by ymo on 2008-12-19
Method 1: Add the following lines to end of /etc/fstab:

/dev/sda6 /mnt/music ext3 defaults 0 1
/dev/sdb1 /mnt/movies ext3 defaults 0 1

Then do:

sudo mkdir /mnt/music /mnt/movies
sudo mount -a

If that works then they will automount each time your system is booted.

Method 2: Find the UUID for your two partitions.

sudo vol_id /dev/sda6
sudo vol_id /dev/sdb1

then add following lines to /etc/fstab

UUID=xxxxxxx /mnt/music ext3 defaults 0 1
UUID=yyyyyyy /mnt/movies ext3 defaults 0 1

where xxxxxxx and yyyyyyy are the ID_FS_UUID values returned by vol_id.

Then do:

sudo mkdir /mnt/music /mnt/movies
sudo mount -a

Of course you can change the mount points from /mnt/xxxx to whatever you were using when you manually mounted the vols. You can also change the "defaults" mount options to something else if you want.

---

### Post by drs305 on 2008-12-19
Edit: Beaten to it.

Back up fstab:
```

sudo cp /etc/fstab /etc/fstab.backup

```
Open fstab with root privileges (in ubuntu, it's gksudo gedit) and add these lines:
```

# /dev/sda6
/dev/sda6 /media/mymusic ext3 defaults,users 0 2
# /dev/sdb1
/dev/sdb1 /media/mymountpoint ext3 defaults,users 0 2

```
Save the file.


Make sure the directories exist. Change the *mymusic* and *mymountpoint* names thoughout. Substitute your username:
```

sudo mkdir /media/mymusic /media/mymountpoint
sudo chown -R yourusername: /media/mymusic /media/mymountpoint
chmod -R 750 /media/mymusic /media/mymountpoint

```

Mount the devices:
```
sudo mount -a
```

Recommend using UUIDs, given in the example above. Obtain the UUIDs with the command "sudo blkid".

---

### Post by tarvinder on 2008-12-20
Thank You to all three of you: DamonChyld, ymo and drs305. Wow, 3 people came up with so many methods of mounting drive. Now, I'm able to mount the drives. Thanks again. I will keep all three methods in my diary, for use in future.

---

### Post by npaisnel on 2009-02-22
Is there not a way to do this totally through the GUI?  
I am sure in Ubuntu iI remember doing it all via the GUI, and then just checking the fstab file to make sure it all looked ok?

I have just installed Xubuntu on an old machine to stick into the workshop to act as a music player and ran in to this same problem again.  I have not used Ubuntu or variants for a good while...since 6.04 I think, so I could not remember how to add the second data disk...hence finding this thread.

Does Xubuntu have the same app that Ubuntu had (or I think it had) to do this?  If any one knows what app I mean can you remind us all of the name of it and whether it is suitable to add to Xubuntu.

Thanks

Neil

---

### Post by Elfy on 2009-02-22
Possibly you are talking about [PySDM]("http://ubuntuforums.org/showthread.php?t=872197")

Personally I would much rather do it by editing fstab.

In this thread people talk about mounting /media and /mnt - if you don't know the difference then using /media/mountpoint will show it on the desktop.

---

### Post by npaisnel on 2009-02-22
Thanks for that, but no it was not that,  I thought it was one of the disk utilities built into Ubuntu, part of the disk/system management pages.

 I can understand why you say you prefer to edit the fstab file manually, but for people like myself that have done it in the past but do not do cmd line stuff regularly, you need to learn the whole thing over again each time you do it.  Last time it looked at them on my machine was 12 - 18 months ago

My old Ubuntu machine in the workshop running 6.??  has worked fine playing music/videos, pictures, reading pdf instruction files etc, since I set it up a year or more back.. That was the last time I looked at any command line stuff.

GUI is (generally) intuitive, and you do not need to remember which commands to use, where to mount  different media etc etc.  I can go and read a MAN page, but generally they are not specific enough for someone with little or no knowledge of the subject and syntax required.

Will try PySDM  though, thanks

Neil

---

