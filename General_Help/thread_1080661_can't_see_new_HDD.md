---
title: "can't see new HDD"
date: 2009-02-25
forum: General Help
---

### Post by mongoose_za on 2009-02-25
Hi,

Just bought a 1.5 Terabyte HDD but I can't see it in Linux.

How can I fix this?

I've got Ubuntu 8.04 Hardy Heron.

Thanks,

---

### Post by taurus on 2009-02-25
Is it internal or external drive?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Peter09 on 2009-02-25
Can you post the output of the terminal commands

```
lshw -C storage
```

and

```
df -l
```

---

### Post by jimmyhacker on 2009-02-25
dude if you dont want to get resolved your problem then stop making us to wait you and leave forum.2 members tried to resolve then you don`t answer us.what`s your problem.I tryin to not be ignorant but u must watch your thread or just mark it solved.i had same problem.if your new hard disk is partitioned then try

1-mkdir /newhd

mount /dev/sda1 /newhd rw
mount /dev/hda1 /newhd rw

---

### Post by mb_webguy on 2009-02-25
> **jimmyhacker said:**
> dude if you dont want to get resolved your problem then stop making us to wait you and leave forum.2 members tried to resolve then you don`t answer us.what`s your problem.I tryin to not be ignorant but u must watch your thread or just mark it solved.i had same problem.if your new hard disk is partitioned then try

1-mkdir /newhd

mount /dev/sda1 /newhd rw
mount /dev/hda1 /newhd rw

Dude, chill.  It's been less than an hour since he made his first post.  We advise people not to bump their posts more often than every 12 hours or so, and so I don't think we should then expect them to sit and watch the forum obsessively for someone to respond to their post.

Besides, it's his problem, not yours.  If he's not in a rush to fix the problem, why should you be?

---

### Post by mongoose_za on 2009-02-26
taurus, Peter09 and mb_webguy thank you I will try this as soon as I get home after work later. I will then post the responses. Just incase, I want to make sure these commands won't format or anything like that because there is a lot of information on the HDD. Oh and It's an **internal **SATA 2 Seagate Barracuda.

As for jimmyhacker, I happy your so enthusiastic for me to solve my problem. I actually posted, went to sleep, arrived at work now and will get right to it when I'm home. If that is ok with you of course.

---

### Post by mongoose_za on 2009-03-01
> Is it internal or external drive?
external

> sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea732d2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10443    83883366    7  HPFS/NTFS
/dev/sda2           10444       13054    20971520    7  HPFS/NTFS
/dev/sda3           13054       30402   139340800    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cc817f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14594   117218400+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98ee98ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       13131   105474726    7  HPFS/NTFS
/dev/sdc2           13132       14593    11743515    5  Extended
/dev/sdc5           13132       14347     9767488+  83  Linux
/dev/sdc6           14348       14593     1975963+  82  Linux swap / Solaris

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8d69945

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd2   *           2      182401  1465128000    5  Extended
/dev/sdd5               2      182401  1465127968+   7  HPFS/NTFS


> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=d778ed24-877f-45d0-b7d3-1c692993765c /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=39292949-2953-4e92-81a0-ea43c18a9747 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc5             9.2G  2.1G  6.7G  24% /
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   84K  1.7G   1% /dev
devshm                1.7G   12K  1.7G   1% /dev/shm
lrm                   1.7G   38M  1.6G   3% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      9.2G  2.1G  6.7G  24% /home/mongi/.gvfs
/dev/sda3             133G   98G   36G  74% /media/Games


> lshw -C storage
WARNING: you should run this program as super-user.
  *-ide                   
       description: IDE interface
       product: 88SE6121 SATA II Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b2
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master cap_list
       configuration: driver=ata_generic latency=0 module=ata_generic
  *-ide:0
       description: IDE interface
       product: ICH10 4 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ide bus_master cap_list
       configuration: driver=ata_generic latency=0 module=ata_generic
  *-ide:1
       description: IDE interface
       product: ICH10 2 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ide bus_master cap_list
       configuration: driver=ata_generic latency=0 module=ata_generic


> df -l

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc5              9614116   2156816   6968928  24% /
varrun                 1684756       104   1684652   1% /var/run
varlock                1684756         0   1684756   0% /var/lock
udev                   1684756        84   1684672   1% /dev
devshm                 1684756        12   1684744   1% /dev/shm
lrm                    1684756     38176   1646580   3% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon       9614116   2156816   6968928  24% /home/mongi/.gvfs
/dev/sda3            139340796 102285824  37054972  74% /media/Games



> 1-mkdir /newhd
mount /dev/sda1 /newhd rw
mount /dev/hda1 /newhd rw
Didn't return any results and not sure what I was supposed to do with these commands.

---

### Post by taurus on 2009-03-01
```
sudo mkdir /media/sdd5
sudo mount -t ntfs-3g /dev/sdd5 /media/sdd5
df -h
```

---

### Post by mongoose_za on 2009-03-01
taurus your a genius I can see it. It moved all my drivers to removeable media and there it is as sdd5 :-D

Would you find just explaining what happened and how you knew what to do?



I rebooted and now the drive is not visible again. Do I have to repeat this process for every startup?

---

### Post by mongoose_za on 2009-03-05
anything i can do so i don't have to keep typing this code every time I log in?

---

### Post by taurus on 2009-03-05
Sounds like you want it mount automatically each time you boot.  Install ntfs-config and use it to configure it.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Otherwise, you can add an entry in /etc/fstab by hand if you wish.

---

### Post by mongoose_za on 2009-03-05
hmmm when i use ntfs-config i have three partitions that i can configure.
/dev/sdc1 <Click here to slect a mount point>
/dev/sd3 /media/Games
/dev/sda1 <Click here to slect a mount point>

But I don't recognise these being the partition I actually want to mount. I want to mount sdd5 which is the big one.

I have tried before actually mounting sdd5 and after but ntfs-config doesn't see it.

---

### Post by taurus on 2009-03-05
Just edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdd5   /media/sdd5   ntfs-3g   defaults,locale=**en_US**.UTF-8  0  0
```
Assuming you are in the US.

Save it and reboot.

Or you can replace the /dev/sdd5 in /etc/fstab with the UUID for that partition.

```
sudo blkid
```

---

### Post by mongoose_za on 2009-03-07
Thanks taurus,
You are really good with this stuff and I'm greatful you could help me.

---

