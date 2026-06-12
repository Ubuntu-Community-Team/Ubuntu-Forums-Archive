---
title: "[SOLVED] Problem mounting NTFS hard drives"
date: 2008-12-17
forum: General Help
---

### Post by ejunooni on 2008-12-17
I am new to ubuntu, so be patient if I am unable to describe my problem correctly.

Here is some information about my system
I am running 32-bit ubuntu 8.10 on a quad core machine.
I have 3 hard drives.

1 is dedicated to ubuntu which is a SATA drive. the other 2 are NTFS from my old windows machine which are IDE.
Here is an fdisk -l output of my drives


```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045d6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24418768+  83  Linux
/dev/sda2            3041       30401   219777232+   5  Extended
/dev/sda5            3041        3654     4931923+  82  Linux swap / Solaris
/dev/sda6            3655        3690      289138+  83  Linux
/dev/sda7            3691       18243   116896941   83  Linux
/dev/sda8           18244       18486     1951866   83  Linux
/dev/sda9           18487       30401    95707206   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa0b519f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24d124d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS

```

I have mounted the 2 NTFS drives by adding the following entries in my /etc/fstab

```

#/dev/sdb1
/dev/sdb1	/media/Video	ntfs-3g	uid=1000,gid=1000,umask=0022	0	0
# /dev/sdc1
/dev/sdc1	/media/Audio	ntfs-3g	uid=1000,gid=1000,umask=0022	0	0

```


Now, some times when i start up my machine the drives are mounted correctly without any problems but at other times when i browse to /media folder i see the mounted drives as Video and Video_ and Video is actually the Audio drive and Video_ is the real Video drive.

When that happened i did another fdisk -l and found out that this time around 

sda1 was Video, sdb1 was Audio and sdc were my linux drives.

Now i am not sure why they dont get the same hard drive letter assigned every time i restart.

Is this something to do with ubuntu or do i need to check the jumper settings on my hard drives? because i believe they are set to cable select for primary.


Sorry for the long post and thanks in advance for the help!

---

### Post by taurus on 2008-12-17
Instead of using /dev/sdb1 & /dev/sdc1 in /etc/fstab, you can use the UUIDs for those two harddrives.

```
sudo blkid
```

---

### Post by jerome1232 on 2008-12-17
You could refer to them in your fstab by blkid instead of device path.

use 'sudo blkid' to show the devices and their blkid, replace /dev/sdxx with the blkid in your fstab and they won't flip flop anymore.

Feel free to ask questions if I'm not being clear enough ;)

---

### Post by ejunooni on 2008-12-17
I just did that and it seems like Video drive is mounted correctly but not the Audio.

when i click on it, I get an error message 

Cannot Mount Volume
You are not privileged to mount volume /media/Audio

and after a few seconds this shows up

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by taurus on 2008-12-17
Can you post the outputs of these commands?

```
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by ejunooni on 2008-12-17
blkid output:

```
/dev/sda1: UUID="6A46B35546B3212D" LABEL="Video" TYPE="ntfs" 
/dev/sdb1: UUID="B604588E04585409" LABEL="Audio" TYPE="ntfs" 
/dev/sdc1: UUID="1eaf0fda-8a07-4f08-9690-f485d8d3cf18" TYPE="ext3" 
/dev/sdd1: UUID="B02D-A390" TYPE="vfat" 
/dev/sdc5: TYPE="swap" UUID="bd453327-5f60-4d5f-aeae-a6c2be395645" 
/dev/sdc6: UUID="7d59e2f5-a6e5-4a04-9594-983b26c3c5c6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc7: UUID="f0ac3277-7fc9-44c6-9423-5ce786fadaaa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc8: UUID="ba1f5612-ae40-4a0c-9107-712eb0536522" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc9: UUID="6507ba96-ccda-46f6-b136-5faf4a8ff0d5" SEC_TYPE="ext2" TYPE="ext3" 

```

cat /etc/fstab output:

 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1eaf0fda-8a07-4f08-9690-f485d8d3cf18 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7d59e2f5-a6e5-4a04-9594-983b26c3c5c6 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=f0ac3277-7fc9-44c6-9423-5ce786fadaaa /home           ext3    relatime        0       2
# /dev/sda8
UUID=ba1f5612-ae40-4a0c-9107-712eb0536522 /tmp            ext3    relatime        0       2
# /dev/sda9
UUID=6507ba96-ccda-46f6-b136-5faf4a8ff0d5 /vmware         ext3    relatime        0       2
# /dev/sda5
UUID=bd453327-5f60-4d5f-aeae-a6c2be395645 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=6A46B35546B3212D	/media/Video	ntfs-3g	uid=1000,gid=1000,umask=0022	0	0
# /dev/sdc1
UUID=B604588E04585409	/media/Audio	ntfs-3g	uid=1000,gid=1000,umask=0022	0	0

```

df -h output


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              23G  4.1G   18G  19% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  360K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  248K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc6             274M   34M  226M  13% /boot
/dev/sdc7             110G   32G   73G  31% /home
/dev/sdc8             1.9G   44M  1.7G   3% /tmp
/dev/sdc9              90G   12G   74G  14% /vmware
/dev/sda1             299G  245G   55G  82% /media/Video
/dev/scd0             699M  699M     0 100% /media/cdrom0

```

---

### Post by jerome1232 on 2008-12-17
> **ejunooni said:**
> blkid output:

```
/dev/sda1: UUID="6A46B35546B3212D" LABEL="Video" TYPE="ntfs" 
/dev/sdb1: UUID="B604588E04585409" LABEL="Audio" TYPE="ntfs" 
/dev/sdc1: UUID="[COLOR="#ff0000"]1eaf0fda-8a07-4f08-9690-f485d8d3cf18[/COLOR]" TYPE="ext3" 
/dev/sdd1: UUID="B02D-A390" TYPE="vfat" 
/dev/sdc5: TYPE="swap" UUID="bd453327-5f60-4d5f-aeae-a6c2be395645" 
/dev/sdc6: UUID="7d59e2f5-a6e5-4a04-9594-983b26c3c5c6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc7: UUID="f0ac3277-7fc9-44c6-9423-5ce786fadaaa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc8: UUID="ba1f5612-ae40-4a0c-9107-712eb0536522" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc9: UUID="6507ba96-ccda-46f6-b136-5faf4a8ff0d5" SEC_TYPE="ext2" TYPE="ext3" 

```

cat /etc/fstab output:

 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1eaf0fda-8a07-4f08-9690-f485d8d3cf18 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7d59e2f5-a6e5-4a04-9594-983b26c3c5c6 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=f0ac3277-7fc9-44c6-9423-5ce786fadaaa /home           ext3    relatime        0       2
# /dev/sda8
UUID=ba1f5612-ae40-4a0c-9107-712eb0536522 /tmp            ext3    relatime        0       2
# /dev/sda9
UUID=6507ba96-ccda-46f6-b136-5faf4a8ff0d5 /vmware         ext3    relatime        0       2
# /dev/sda5
UUID=bd453327-5f60-4d5f-aeae-a6c2be395645 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=6A46B35546B3212D	/media/Video	ntfs-3g	uid=1000,gid=1000,umask=0022	0	0
# /dev/sdc1
[COLOR="Red"]UUID=B604588E04585409[/COLOR]	/media/Audio	ntfs-3g	uid=1000,gid=1000,umask=0022	0	0

```

df -h output


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              23G  4.1G   18G  19% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  360K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  248K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc6             274M   34M  226M  13% /boot
/dev/sdc7             110G   32G   73G  31% /home
/dev/sdc8             1.9G   44M  1.7G   3% /tmp
/dev/sdc9              90G   12G   74G  14% /vmware
/dev/sda1             299G  245G   55G  82% /media/Video
/dev/scd0             699M  699M     0 100% /media/cdrom0

```

I believe your problem is hihglighted in red

---

### Post by ejunooni on 2008-12-17
but why is sdc1 showing as ext3 in blkid output then? while my audio drive is ntfs which should be sdb1

---

### Post by taurus on 2008-12-17
> **jerome1232 said:**
> I believe your problem is hihglighted in red

Are you sure because that is his root partition?

```

UUID=1eaf0fda-8a07-4f08-9690-f485d8d3cf18 /               ext3    relatime,errors=remount-ro 0       1

```

---

### Post by jerome1232 on 2008-12-17
Yeah your right I guess I glanced too quickly at the comment #/dev/sdc1 and at the blkid's and saw a missmatch, I didn't look at the whole thing closely. Everything looks fine to me on a second closer look. I don't see why you would be getting an error.

On another note you can refer to the drives by their labels as well.

---

### Post by ejunooni on 2008-12-18
anyone else got any ideas?

---

### Post by ejunooni on 2008-12-20
I restarted a couple of times and it seems to be mounting correctly. Hopefully statys this way.

Thanks for your help.

---

