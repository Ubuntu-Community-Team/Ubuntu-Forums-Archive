---
title: "Trouble adding new hard disk"
date: 2009-02-22
forum: General Help
---

### Post by Cheesemill on 2009-02-22
Hi there guys,

I'm having trouble adding a new hard disk to my Ubuntu 8.10 system.
My current disk setup is as follows:

Primary Master:
120GB IDE System drive mounted as / and swap (sdb)

Secondary Slave:
120GB IDE mounted as /media/scratch (sdc1)

RAID Card:
700GB RAID 5 mounted as /media/raid (sda1)

All of the above were set up during installation.


I'm trying to add a 250GB IDE drive on the Primary Slave channel, but every time I plug it in the system refuses to boot saying that the root device doesn't exist. The current drives are defined in fstab using UUID's which I was led to believe don't change when adding / removing drives. The new drive is correctly recognized in the BIOS so this isn't the problem.

Any help would be much appreciated.

Cheesemill.

---

### Post by kmac on 2009-02-22
Does the device show up in logs? Or what do you get with fdisk -l (L)?

---

### Post by fjgaude on 2009-02-22
Are you sure the BIOS points to /sdb drive to boot from? That drive has to have the priority in the sequence of selecting which device to handle the boot up.

---

### Post by Cheesemill on 2009-02-22
The boot order is definitely correct, GRUB loads fine but then the computer hangs at the splash screen with the following error:

ALERT! /dev/disk/by-uuid/c78f264f-2c0d-4ac7-a8cf-aada70d0f145 does not exist. Dropping to shell!

---

### Post by fjgaude on 2009-02-22
Show us what these look like:

```
sudo fdisk -l
```

and

```
cat /etc/fstab
```

We can then go from there.

---

### Post by Cheesemill on 2009-02-22
> **fjgaude said:**
> Show us what these look like:

```
sudo fdisk -l
```

and

```
cat /etc/fstab
```

We can then go from there.


Hi fjgaude,

I can give you the following results but I don't think they'll be any use, I can only boot my system into a usable state without the new drive.

I can only get as far as a busybox shell with the new drive attached which doesn't include fdisk.

I've used my gparted live CD to check that the drive is operational, it's showing up as a sdx device with 250GB of empty space which is correct.

Unfortunately I've never been able to use any Ubuntu Live CD's on this machine so that isn't an option (I installed with the alternate CD).


Results from working system (without new HD)

fdisk -l
```
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00550054

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13991   112382676   83  Linux
/dev/sda2           13992       14589     4803435    5  Extended
/dev/sda5           13992       14589     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1a8fe69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14589   117186111   83  Linux

Disk /dev/sdc: 750.1 GB, 750124007424 bytes
255 heads, 63 sectors/track, 91197 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc31bc26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91198   732540928    7  HPFS/NTFS
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c78f264f-2c0d-4ac7-a8cf-aada70d0f145 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=848AE4CC8AE4BC34 /media/raid     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=bb415629-2cda-40b6-a0f7-4a3dfdff8bf6 /media/scratch  ext3    relatime        0       2
# /dev/sda5
UUID=48bac956-9c80-4959-aff1-1fd1a4de32a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Drive letter assignments have changed since my first post because I've altered thee boot preference in my BIOS.

Cheesemill.

---

### Post by fjgaude on 2009-02-22
ALERT! /dev/disk/by-uuid/c78f264f-2c0d-4ac7-a8cf-aada70d0f145 does not exist. Dropping to shell!

The above UUID doesn't show in fdisk listing. It is the UUID of the drive that doesn't permit booting after you connect it?

It must be logged into the system somewhere. Try this:

```
ls /dev/disk/by-uuid
```

Then this:

```
sudo blkid
```

These two command will show all the drives. I guess you will have to do this from your gparted disk. You might have to **apt-get** the **blkid** to use that command.

The fact that you can't use Ubuntu liveCD to install tells us something, but can't say waht!

---

### Post by Cheesemill on 2009-02-22
> **fjgaude said:**
> ALERT! /dev/disk/by-uuid/c78f264f-2c0d-4ac7-a8cf-aada70d0f145 does not exist. Dropping to shell!

The above UUID doesn't show in fdisk listing. It is the UUID of the drive that doesn't permit booting after you connect it?



If you look at my fstab it mounts c78f264f-2c0d-4ac7-a8cf-aada70d0f145 as / (sda1) which is correct.

The problem is that the system cannot find that disk by UUID when booting with the new disk attached.

Cheesemill

---

### Post by fjgaude on 2009-02-22
Understand... but there is something strange going on here. Without the new drive you normally boot from /sda1 with /sda5 as swap, or is it /sdb1 and /sdb5?

Is there anyway for you to run the two commands I suggested, with the new drive connected?

Something changes when you add the new drive. We have to find out what, eh?

And you can't boot using the normal Ubuntu install liveCD? Strange?

You created the raid5 using software that came with the card? This is not BIOS created raid is it?

---

### Post by Cheesemill on 2009-02-23
There's definitely something strange going on !!!

I realised that I hadn't actually tried a Live 8.10 CD, it was a while back when I was installing 8.04 that I had problems with it. So I tried an 8.10 Live CD on my working system and it was all fine.

Brilliant, I thought. I'll just plug in the new disk and give you the results of my fdisk.

Would you believe it, booting my system from the Live CD with the new disk attached resulted in being dropped to a BusyBox shell :(

I really have no idea what the problem is so I may just try adding the new disk to my hardware RAID 5 instead.

Cheesemill.

---

### Post by fjgaude on 2009-02-23
How are the raid card used to create the raid5 array? Did you create the array?

So much to learn, eh?

---

### Post by Cheesemill on 2009-02-23
The RAID card is a Dell (LSI Logic) CERC ATA-100 IDE RAID which I believe is hardware RAID (I got it out of my old 400SC server).

I created the RAID using the card's BIOS, it's a RAID 5 with 4 x 250GB drives.

---

### Post by Slim Odds on 2009-02-23
Are you sure that the drives have their jumpers set properly to act as master and slave?

It sounds like maybe both are set to master and are fighting each other.

---

### Post by Cheesemill on 2009-02-23
Jumpers are correct, I've just double-checked them.
The drives are being reported properly in the BIOS

I'll have a rummage about for a Win PE or Windows installation disk and try that to see if we can completely rule out hardware errors.

---

### Post by fjgaude on 2009-02-23
> **Cheesemill said:**
> The RAID card is a Dell (LSI Logic) CERC ATA-100 IDE RAID which I believe is hardware RAID (I got it out of my old 400SC server).

I created the RAID using the card's BIOS, it's a RAID 5 with 4 x 250GB drives.

And when installing Ubuntu you had the raid recognized by the OS, as /sdc1 or what?

Something is just not right here, with what you have told us. Can't you run the **blkid** command?

---

