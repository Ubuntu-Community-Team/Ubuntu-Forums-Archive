---
title: "Cant find harddrive! please help :)"
date: 2008-12-27
forum: Desktop Environments
---

### Post by Lighto on 2008-12-27
I installed ubuntu to my C:\ drive and everything works and i can see my old windows D drive and that can be mounted and works too but my F:\ drive is missing completely!.

I know whats wrong with my F:\ it was formatted in windows but i didnt give it a filesystem like NTFS etc i just left it formatted to blank.... I thought i could format it once i was in ubuntu which i was wrong... At least as far as i know..

I need a way to make ubuntu find my harddrive that is formatted but not given a file system so i can format it to ext3(?) and use in ubuntu.

I repeat im already in ubuntu and it is working i just need it to find, format and make my old harddrive available... In windows i could use partitino magic to do this... How can i do this in ubuntu?

Note - Im using ubuntu 8.10 and my harddrive im trying to find is 500 GB... if any of this is relevent.

Thanks :)
Lighto

---

### Post by logos34 on 2008-12-27
post the output of 

sudo fdisk -l

hopefully it will show up and you can just [format it and add mount point]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by Lighto on 2008-12-27
> **logos34 said:**
> post the output of 

sudo fdisk -l

hopefully it will show up and you can just [format it and add mount point]("http://www.psychocats.net/ubuntu/mountlinux")

root@lighto-desktop:~# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbee8bee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe66537de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       60801   488376000    f  W95 Ext'd (LBA)

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0894946f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         542     4097488+   b  W95 FAT32

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa9ffa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60045   482311431   83  Linux
/dev/sdd2           60046       60801     6072570    5  Extended
/dev/sdd5           60046       60801     6072538+  82  Linux swap / Solaris

// Says this

// Note the 500 GB i mentioned is made from two 250 GB harddrives joined together...

---

### Post by jerome1232 on 2008-12-27
Okay so right now you have 4 disks attached. It looks like every single one of them has a filesystem so it just needs to be mounted.

Are you sure these aren't showing up in your places menu? Usually any disk that isn't in fstab will show up there.

I assume that sda1 is your Windows C: drive since it's ntfs, sdb1 and sdc1 are both  fat32 so one of those must be the f: drive your refering to. 

sdd1 looks to be your root filesystem.

If you want sdb1 and sdc1 to mount at boot time you will need to modify your fstab but first try and mount them and make sure they are working

```
sudo mkdir /media/sdb1; sudo mkdir /media/sdc1
sudo mount /dev/sdb1 /media/sdb1 -o umask=000; sudo mount /dev/sdc1 /media/sdc1 -o umask=000
```

They should show up on your desktop let me know if it's working and then we can get fstab going.

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Okay so right now you have 4 disks attached. It looks like every single one of them has a filesystem so it just needs to be mounted.

Are you sure these aren't showing up in your places menu? Usually any disk that isn't in fstab will show up there.

I assume that sda1 is your Windows C: drive since it's ntfs, sdb1 and sdc1 are both  fat32 so one of those must be the f: drive your refering to. 

sdd1 looks to be your root filesystem.

If you want sdb1 and sdc1 to mount at boot time you will need to modify your fstab but first try and mount them and make sure they are working

```
sudo mkdir /media/sdb1; sudo mkdir /media/sdc1
sudo mount /dev/sdb1 /media/sdb1 -o umask=000; sudo mount /dev/sdc1 /media/sdc1 -o umask=000
```

They should show up on your desktop let me know if it's working and then we can get fstab going.

They are not available in places... Im trying GParted like the help page said but its taking a long time to *scanning for drives*.

---

### Post by Lighto on 2008-12-27
GParted is still loading.... this may take hours? Is there a faster way?

Thanks,
Lighto

---

### Post by jerome1232 on 2008-12-27
It shouldn't be taking that long, I know there  was (is?) a bug that if your bios says there's a floppy drive but you don't really have one, gparted will wait ages for that floppy drive before realizing it's not there. I recall fixing it by telling my bios to report no fdd to the OS (this is just a shot in the dark as to why gparted is taking so long to load for you)

In the meantime why don't you try mounting the disks?

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> It shouldn't be taking that long, I know there  was (is?) a bug that if your bios says there's a floppy drive but you don't really have one, gparted will wait ages for that floppy drive before realizing it's not there. I recall fixing it by telling my bios to report no fdd to the OS (this is just a shot in the dark as to why gparted is taking so long to load for you)

In the meantime why don't you try mounting the disks?

I see no option to mount especially not in "Places" and yes i dont have a floppy drive.... Maybe thats the problem?

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> 
// Note the 500 GB i mentioned is made from two 250 GB harddrives joined together...

Can you give some more info about this ?
Is it hardware-RAID or fake-raid ?
Do you have more than 4 physical disks attached to/in your machine ?

---

### Post by Lighto on 2008-12-27
> **albinootje said:**
> Can you give some more info about this ?
Is it hardware-RAID or fake-raid ?
Do you have more than 4 physical disks attached to/in your machine ?

I have 4 hard drives and its hardware raid

---

### Post by tad1073 on 2008-12-27
Have you looked in /media

---

### Post by Lighto on 2008-12-27
> **tad1073 said:**
> Have you looked in /media

yup just the cds, and disks i can use from places not the other one

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> I have 4 hard drives and its hardware raid

Thanks. Can you post the output of this :
```

blkid 

```

---

### Post by Lighto on 2008-12-27
/dev/sdb1: LABEL="TEST-DOS" UUID="3108-1EEA" TYPE="vfat" 
/dev/sdc1: LABEL="TEST-DOS" UUID="3108-1EEA" TYPE="vfat" 
/dev/sdd1: UUID="0ec02cdd-d731-4e2e-a1f0-13e56644391d" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7EA0787BA0783C29" TYPE="ntfs" 
/dev/sdd5: TYPE="swap" UUID="981ee0b8-0b11-46e7-ae16-f8bf3ac96665" 
/dev/sde1: UUID="423826E33826D5A7" LABEL="Storage (External)" TYPE="ntfs"

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> /dev/sdb1: LABEL="TEST-DOS" UUID="3108-1EEA" TYPE="vfat" 
/dev/sdc1: LABEL="TEST-DOS" UUID="3108-1EEA" TYPE="vfat" 
/dev/sdd1: UUID="0ec02cdd-d731-4e2e-a1f0-13e56644391d" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7EA0787BA0783C29" TYPE="ntfs" 
/dev/sdd5: TYPE="swap" UUID="981ee0b8-0b11-46e7-ae16-f8bf3ac96665" 
/dev/sde1: UUID="423826E33826D5A7" LABEL="Storage (External)" TYPE="ntfs"

Can you try :
```

sudo mkdir /media/storage-external
sudo mount /dev/sde1 /media/storage-external -t ntfs-3g -o force,umask=000

```
And then browse in /media with your file-manager.

---

### Post by Lighto on 2008-12-27
> **albinootje said:**
> Can you try :
```

sudo mkdir /media/storage-external
sudo mount /dev/sde1 /media/storage-external -t ntfs-3g -o force,umask=000

```
And then browse in /media with your file-manager.

that drive (storage external) was already available from "places"....

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> that drive (storage external) was already available from "places"....

Hmmm, sorry.
Please try jerome1232's mount command suggestion.

---

### Post by jerome1232 on 2008-12-27
If you looked at my post you'd see at the end I showed you how to mount the disks, /dev/sdb1 and /dev/sdc1 but are those supposed to be in a raid?

If that's the case I don't have experience with setting that up! I think you'll need to look at FAKEraid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Okay so right now you have 4 disks attached. It looks like every single one of them has a filesystem so it just needs to be mounted.

Are you sure these aren't showing up in your places menu? Usually any disk that isn't in fstab will show up there.

I assume that sda1 is your Windows C: drive since it's ntfs, sdb1 and sdc1 are both  fat32 so one of those must be the f: drive your refering to. 

sdd1 looks to be your root filesystem.

If you want sdb1 and sdc1 to mount at boot time you will need to modify your fstab but first try and mount them and make sure they are working

```
sudo mkdir /media/sdb1; sudo mkdir /media/sdc1
sudo mount /dev/sdb1 /media/sdb1 -o umask=000; sudo mount /dev/sdc1 /media/sdc1 -o umask=000
```

They should show up on your desktop let me know if it's working and then we can get fstab going.

// I tried this command
sudo mount /dev/sdb1 /media/sdb1 -o umask=000; sudo mount /dev/sdc1 /media/sdc1 -o umask=000
// mount: you must specify the filesystem type

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> If you looked at my post you'd see at the end I showed you how to mount the disks, /dev/sdb1 and /dev/sdc1 but are those supposed to be in a raid?

If that's the case I don't have experience with setting that up! I think you'll need to look at FAKEraid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Im 99.99% sure all i need to do is find the drives and format them.... its just the partitions were deleted from them in windows before i loaded ubuntu.... i should have left them but since windows is *gone* i cant just format it to NTFS or something since ubuntu is not finding it in a way i can format it...

---

### Post by jerome1232 on 2008-12-27
Then try specifying the file system but once agian if those two disks are in a RAID together, you will need to setup fakeRAID to get them to correctly show as one disk.

```
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000; sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
```

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Then try specifying the file system but once agian if those two disks are in a RAID together, you will need to setup FAKEraid to get them to correctly show as one disk.

```
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000; sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
```

i dont care if its 1 disk or 2... as long as it works :) (2 would be better... less chance of major problem if one screws up)

Note - This command failed also it mounted a 8 GB disk TEST-DOS that seems irrelevent

It also gave following error :
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Then try specifying the file system but once agian if those two disks are in a RAID together, you will need to setup FAKEraid to get them to correctly show as one disk.

```
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000; sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
```

I just want it to show as 2 seperate 250 GB disks that i can format to linux and start filling up.... -.-

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> I just want it to show as 2 seperate 250 GB disks that i can format to linux and start filling up.... -.-

I wonder whether you are really using hardware RAID.
I think you might be using fakeRAID..

Can you post the output of :
```

lspci
ls -la /dev/mapper*
ls -la /dev/md*

```
Also,please tell us the name of your RAID-card.
And Is it onboard or a separate card ?

---

### Post by Lighto on 2008-12-27
// lspci BELOW
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
03:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
03:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
// lspci ABOVE

// Rest
root@lighto-desktop:~# ls -la /dev/mapper*
ls: cannot access /dev/mapper*: No such file or directory
root@lighto-desktop:~# ls -la /dev/md*
ls: cannot access /dev/md*: No such file or directory

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> 
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)


Thanks.
The first hit from a quick search-engine search already showed this :

[http://osdir.com/ml/linux.ataraid/2007-05/msg00005.html](http://osdir.com/ml/linux.ataraid/2007-05/msg00005.html)

> 
i've tried to get dmraid working with my setup, which is an Intel ICH7
(fake)raid5 on Ubuntu 7.04.


Please make proper backups first before continuing, and carefully read the fakeRAID howto.
GL!

---

### Post by jerome1232 on 2008-12-27
Correct me if I'm wrong but if you want to use them as individual normal drives. 

You will have to take the drives out of the raid array in your (assuming these are onboard controllers) BIOS first. Then reformat them.

---

### Post by Lighto on 2008-12-27
> **albinootje said:**
> Thanks.
The first hit from a quick search-engine search already showed this :

[http://osdir.com/ml/linux.ataraid/2007-05/msg00005.html](http://osdir.com/ml/linux.ataraid/2007-05/msg00005.html)



Please make proper backups first before continuing, and carefully read the fakeRAID howto.
GL!

Doesnt that seem a bit unnecessary (patched kernels etc??? oh my)? cant i just format and mount the disks?

Note - Ive already seen one of these 250 GB hard drives mounted in ubuntu when i FIRST installed ubuntu... but i deleted the partitions and reinstalled ubuntu because i wanted it on a single 500 GB disk... I accomplished that then i wanted the 2 250 GB disks available for storage and they are currently *missing* probably because i deleted the partitions from them with Fdisk (windows command prompt).

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Correct me if I'm wrong but if you want to use them as individual normal drives. 

You will have to take the drives out of the raid array in your (assuming these are onboard controllers) BIOS first. Then reformat them.

So a raid array is loading them as one drive? hmm

Note - I saw something about a RAID on setup on bios although it warns any changes to this will destroy all data on all hard drives... Sounds like fun.

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> So a raid array is loading them as one drive? hmm

I just checked at a webserver which I co-admin, which has a real hardware (3ware) RAID card.

There the 5 or more disks in the RAID-array simply show up as 1 disk, as it should :

sudo fdisk -l

Disk /dev/sda: 1599.9 GB, 1599955009536 bytes
255 heads, 63 sectors/track, 194516 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         255     1951897+  82  Linux swap / Solaris
/dev/sda3             256        2687    19535040   83  Linux
/dev/sda4            2688      194516  1540866442+   5  Extended
/dev/sda5            2688       81713   634776313+  83  Linux
/dev/sda6           81714      194516   906090066   83  Linux

So.. I still assume that you are using fakeRAID.

---

### Post by jerome1232 on 2008-12-27
> **Lighto said:**
> So a raid array is loading them as one drive? hmm

Well I'm just going off of what you said, you mentioned earlier that the drive that isn't mounting is 2 250 GB disks combined as one making a 500 GB disk.

The only way I know of to do that is to put them in a RAID 0 or use LVM, since you aren't using LVM I am assuming they are in a RAID 0 and that's what the problem is. 

Many "hardware" raid controllers these days aren't actually hardware raid controllers, they just use a combination of hardware and software to make it seem that it's a hardware raid in Windows, in Linux it's called a fakeRAID.

If you actually haven't put them in a RAID then I am wrong and maybe you just need to reformat them using gparted. 

I don't know which one it is since I didn't configure your system and I don't actually know how it's setup.

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> So a raid array is loading them as one drive? hmm

Note - I saw something about a RAID on setup on bios although it warns any changes to this will destroy all data on all hard drives... Sounds like fun.

Must be more fun than making backups ;-)

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Well I'm just going off of what you said, you mentioned earlier that the drive that isn't mounting is 2 250 GB disks combined as one making a 500 GB disk.

The only way I know of to do that is to put them in a RAID 0 or use LVM, since you aren't using LVM I am assuming they are in a RAID 0 and that's what the problem is. 

Many "hardware" raid controllers these days aren't actually hardware raid controllers, they just use a combination of hardware and software to make it seem that it's a hardware raid in Windows, in Linux it's called a fakeRAID.

If you actually haven't put them in a RAID then I am wrong and maybe you just need to reformat them using gparted. 

I don't know which one it is since I didn't configure your system and I don't actually know how it's setup.

I didnt do anything the computer game with a so called 500 GB hard drive which i found to actually be 2 harddrives of 250 GB... I just want them to appear as 2 seperate 250 GB hard drives in linux...

Thanks,
Lighto

---

### Post by Lighto on 2008-12-27
> **albinootje said:**
> Must be more fun than making backups ;-)

Everything is already backed up lol i was already expecting ubuntu to screw me over and it seems it did!.

I dont care what happens as long as it works in the end and everything is fine in ubuntu with all hard drives available.

///////////////////////////////////////////////

GParted was still loading.... so i closed it and opened it in shell it said
======================
libparted : 1.8.9
======================
Cannot have a partition outside the disk!


Maybe thats why its saying "Searching for drives" for over 2 hours straight?. (floppy is disabled on my bios i checked)

---

### Post by jerome1232 on 2008-12-27
okay, so maybe we are just going off on a tangent about the raid stuff :) 

I wonder why the mount command didn't work then. What's the output of mount right now

```
mount
```

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> okay, so maybe we are just going off on a tangent about the raid stuff :) 

I wonder why the mount command didn't work then. What's the output of mount right now

```
mount
```

Mount says :
/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lighto/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lighto)
/dev/sde1 on /media/Storage (External) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by jerome1232 on 2008-12-27
Okay well I guess you can format it with parted (talk about everything being difficult this is crazy)

```
sudo parted
```

type help and it'll give you a list of commands. I'm not sure why gparted is freaking out

you change devices by typeing 'select /dev/sdb' then work on it.

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> Okay well I guess you can format it with parted (talk about everything being difficult this is crazy)

```
sudo parted
```

type help and it'll give you a list of commands. I'm not sure why gparted is freaking out

you change devices by typeing 'select /dev/sdb' then work on it.

which 2 drives i need to format? u saw stuff i posted...

---

### Post by jerome1232 on 2008-12-27
/dev/sdb and /dev/sdc were the drives that aren't mounted.

---

### Post by Lighto on 2008-12-27
> **jerome1232 said:**
> /dev/sdb and /dev/sdc were the drives that aren't mounted.


  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partititon NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system


what should i type? what ever happened to good ol' "format c: -y"
;/

---

### Post by albinootje on 2008-12-27
> **Lighto said:**
> mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partititon NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system


what should i type? what ever happened to good ol' "format c: -y"
;/

I don't want to interface with the discussion here, but if your machine was in my hands, I would start from scratch, turn off any RAID stuff in the BIOS, and use software RAID for the Linux partitions you want software-RAID for.

And, just in case... 
You do know that RAID0 speeds up things, but if one disk fails, you will lose all data. 

... [Y/n] ? :)

---

### Post by jerome1232 on 2008-12-27
Yes well these tools are bit more advanced and can seem complicated at first. (it can rescue broken partitions and much more)

I'm haven't used parted but i'm in it right now. Remember typing help and then the command will give you more information about the command.

I typed help makepartfs and it tells me what the options do from what I'm looking at you'll want to do this, basically this will make a primary partition formated as fat32 that takes 100% of the available space.
```

delete 1
makepartfs primary fat32 100%
```

---

### Post by Lighto on 2008-12-27
> **albinootje said:**
> I don't want to interface with the discussion here, but if your machine was in my hands, I would start from scratch, turn off any RAID stuff in the BIOS, and use software RAID for the Linux partitions you want software-RAID for.

And, just in case... 
You do know that RAID0 speeds up things, but if one disk fails, you will lose all data. 

... [Y/n] ? :)

indeed im aware thats why id like to seperate the hds :)

I will go try disable raid thing and see what happens....

---

### Post by Lighto on 2008-12-27
> **Lighto said:**
> indeed im aware thats why id like to seperate the hds :)

I will go try disable raid thing and see what happens....

I went to bios and to raid section and it said only single 500 GB hard drive is using it and the 2x 250 GB drives are not using it and there was no delete/disable option for them only for 500 GB hard drive which ubuntu is on...

-.-

Maybe i should install xp or something stupid just to format the disks then install ubuntu again LOL

Thanks,
Lighto

---

### Post by Lighto on 2008-12-27
I went ahead and removed the raid now ubuntu grub has screwed up...
[http://ubuntuforums.org/showthread.php?p=6446978#post6446978](http://ubuntuforums.org/showthread.php?p=6446978#post6446978)

Read that if you can help...

Thanks,
Lighto

---

### Post by Lighto on 2008-12-27
> **Lighto said:**
> I went ahead and removed the raid now ubuntu grub has screwed up...
[http://ubuntuforums.org/showthread.php?p=6446978#post6446978](http://ubuntuforums.org/showthread.php?p=6446978#post6446978)

Read that if you can help...

Thanks,
Lighto


Report : Everything is working now and 2 250 GB drives are working :)

Thanks everybody for help :)

---

