---
title: "Error mouting internal drive (WD 250gb ide)"
date: 2010-05-29
forum: Desktop Environments
---

### Post by DmD09 on 2010-05-29
Hello,

I'm receiving an error while mounting a drive in Ubuntu 10.04.  It's a 250gb WD IDE drive, internal.  I'm using Disk Utility and I receive the following error while clicking on "Mount Volume" - 

An error occurred while performing an operation on "250" (Partition 1 of ATA WDC  WDC250BB-55GUA0).  The operation failed.

 
Details:
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

Under disk utility it says it's device name is /dev/sdb.  I've also tried automounting this with NTFS Config Tool, with no luck (the drive isn't even detected)

I have an external 1.0tb drive that is auto detected (shows on desktop).

Any help would be appreciated, I've used Linux for a year in the past..just gettin back into it again.

Thanks for any help,
DmD

---

### Post by lmarmisa on 2010-05-30
Could you post the outputs of these commands:

> 
sudo fdisk -l

sudo blkid

cat /etc/fstab

cat /etc/mtab


---

### Post by DmD09 on 2010-05-30
Hey, thanks for the quick reply.

When I type sudo fdisk -l I get:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019b47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c9c05cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51ccad35

For sudo blkid:
/dev/sda1: UUID="c5814e7f-8c12-4bc7-9a4f-f966e807cefd" TYPE="ext4" 
/dev/sda5: UUID="63be084f-4dfc-4e91-b77f-483e48e90fff" TYPE="swap" 
/dev/sdb1: LABEL="250" UUID="A2A454E2A454BA8D" TYPE="ntfs" 
/dev/sdc1: LABEL="iKore" UUID="5C8C3FF48C3FC6F4" TYPE="ntfs"

For cat /etc/fstab:  
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sdb1	/	ext4	errors=remount-ro	0	1
/dev/sdc1	/media/iKore	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-80	0
/dev/sda5	none	swap	sw	0	0


And finally for cat /etc/mtab:
***@***-desktop:~$ cat /etc/mtab 
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0
/dev/sdc1 /media/iKore fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/sean/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=sean 0 0

----------------
iKore is my terabyte drive [external].  Thanks for the help.

---

### Post by DmD09 on 2010-05-30
Solved:  I had a buddy help me edit fstab to mount the 250 to a different location.  Thanks for the help!

Sean

---

### Post by lmarmisa on 2010-05-30
One line of your /etc/fstab was wrong:

```

For cat /etc/fstab:  
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
**/dev/sdb1    /    ext4    errors=remount-ro    0    1**
/dev/sdc1    /media/iKore    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-80 0
/dev/sda5    none    swap    sw    0    0


```The correct line would be:

```

For cat /etc/fstab:  
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
 
proc    /proc    proc    nodev,noexec,nosuid    0    0[B]
/dev/sda1    /    ext4    errors=remount-ro    0    1[/B]
/dev/sdc1    /media/iKore    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-80     0
/dev/sda5    none    swap    sw    0    0
 

```In any case, I recommend do not use absolute references for partitions ( /dev/sda1 ) but UUIDS:

```

For cat /etc/fstab:  
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>    <options>       <dump>  <pass>
 
proc    /proc    proc    nodev,noexec,nosuid 0 0
UUID=c5814e7f-8c12-4bc7-9a4f-f966e807cefd    /    ext4    errors=remount-ro 0 1
UUID=5C8C3FF48C3FC6F4 /media/iKore ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-80 0 0
UUID=63be084f-4dfc-4e91-b77f-483e48e90fff none swap sw 0 0
 

```Congratulations if you were able to fix your problem.

---

### Post by ernetgt on 2011-03-02
Hi,
I'm having the same trouble and haven't been able to solve it,  here is the information of my disks.  I'm using Ubuntu 10.4:


***sudo fdisk -l
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xb358b358

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1       14593   117218241    7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000a4c14

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        9325    74895360   83  Linux
/dev/sdb2            9325        9726     3226625    5  Extendida
/dev/sdb5            9325        9726     3226624   82  Linux swap / Solaris

***sudo blkid
/dev/sda1: LABEL="Videos" UUID="ACE891D0E89198E2" TYPE="ntfs" 
/dev/sdb1: UUID="8addd60c-68ff-4d4d-8afe-759a8eea3710" TYPE="ext4" 
/dev/sdb5: UUID="c9442364-2799-44eb-a602-3741fb04425a" TYPE="swap" 

*** cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c9442364-2799-44eb-a602-3741fb04425a none            swap    sw              0       0

***cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/gestor/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=gestor 0 0


I have two disks, when I try to mount the second one (120Gb)  it  gives me this error:
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

Thanks.

---

### Post by arnasd on 2011-05-01
Hi,

I have a problem with logical partition being recognized as removable media and it is being remounted.
dmesg | grep remount shows:

> ard@comp:~$ dmesg | grep remount
[   19.707082] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   24.807371] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   30.862984] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

my /etc/fstab
> ard@comp:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
**UUID=b7c78b73-cd2f-4962-bfd9-82e3278159ba /               ext4    errors=remount-ro 0       1**
# swap was on /dev/sda5 during installation
UUID=7fb4b1f3-0ed3-4d9a-bf1e-7980938611fb none            swap    sw              0       0

> ard@comp:~$ sudo blkid
/dev/sda1: UUID="b7c78b73-cd2f-4962-bfd9-82e3278159ba" TYPE="ext4" 
/dev/sda5: UUID="7fb4b1f3-0ed3-4d9a-bf1e-7980938611fb" TYPE="swap"

I see that logical partition sda1 is recognized correctly, but i assume that fstab has a removable flag marked on that partition. It is shown in places and i get my non-removable partition shown in automount media list. Does anyone know how fstab marks removable and non-removable flags? I couldn't find it.

Is it possible to reconfigure fstab mount point list?

I see that this is common problem and appears for a lot of people but not anyone gets the problem diagnosed.

Thanks,
Arnas

EDIT: I have found out how partition is recognized as removable - using the "Removable Media Bit" [http://ubuntuforums.org/showthread.php?t=1020293](http://ubuntuforums.org/showthread.php?t=1020293)

---

