---
title: "Adding 2nd hard drive, will Ubuntu recognize it?"
date: 2009-02-18
forum: General Help
---

### Post by UranUtan on 2009-02-18
Hi,

If I add a 2nd hard drive (40 GB, IDE). What should I do next when I boot Ubuntu?

Partition layout on current hard drive (160 GB, IDE):
sda1, 10 GB, root (ext3)
sda5, 145 GB, /home (ext3)
sda?, 5 GB, swap

I hope Ubuntu will recognize the new 2nd hard drive. It currently has two NTFS partitions (20 GB primary and 20 GB extended). I would like to delete all these NTFS partitions and create a single 40 GB for Ubuntu.

Can I just open GParted and delete + create a new partition?

Which type of partition and which file system do you recommend?

Thanks in advance for any help.

---

### Post by drs305 on 2009-02-18
When you say you will use it *for* ubuntu, do you mean as an additional drive or for an install.

For an additional drive: Once you have powered it up:
```
sudo fdisk -l
```
It will *probably* be listed as sdb1 and sdb2 - make sure you work with the correct disk.

Open gparted (System, Administration, Partition Editor), delete the current partitions, create a new partition and format it to ext3 (my recommendation  so you get linux permission capability).

Run this to get the UUID:
```
sudo blkid -c /dev/null
```

Make a mount point and make yourself the owner (example name of *data*):
```
sudo mkdir /media/data
sudo chown -R *yourusername:* /media/data
```

Backup fstab and edit, and save when finished:
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```
Add this line (substitute the UUID from earlier command):
> 
UUID=ba83d184-705e-4115-9d42-0823c698a757 /media/data ext3 defaults,users 0 2


Mount it:
```
sudo mount -a
```
If you don't get any messages, the partition is successfully mounted on /media/data

---

### Post by Mercury_Alpha on 2009-02-18
You'll want to set or at least check the jumpers on the back of the hard drives first. Sometimes they're on "Cable Select" by default, which means that their boot order goes according to which one is connected closest on the cable to the motherboard. Most times, though, they're set to "Master," which doesn't work when both are set that way. Most drives these days have jumper diagrams printed on them, and you can also look it up in the manual.

Ext3 is the default file system for Ubuntu.

---

### Post by Slim Odds on 2009-02-18
> **UranUtan said:**
> 
I hope Ubuntu will recognize the new 2nd hard drive. It currently has two NTFS partitions (20 GB primary and 20 GB extended). I would like to delete all these NTFS partitions and create a single 40 GB for Ubuntu.

Can I just open GParted and delete + create a new partition?

Which type of partition and which file system do you recommend?


No reason it wouldn't
Yes, you can use GParted, although you could also just fdisk
Primary partition, whole disk, ext3 file system.

The tricky part is fstab.

Find the UUID. I think that easiest is ```
sudo tune2fs -l /dev/{put your device here}
```You can find your device with:```
sudo fdisk -l
```Then just copy one of your other entries in fstab and replace the UUID and mount point

Before you mount, create the location where you want to put it: ```
sudo mkdir /{where you want it}
```Then you should be able to:```
sudo mount -a
```

---

### Post by Slim Odds on 2009-02-18
I wouldn't recomment using /media/{anything} for the mount point.

/media is where Ubuntu puts **removable** drives like FLASH cards, USB drives, etc.

Best not to mix apples and oranges.

---

### Post by UranUtan on 2009-02-18
Hi,

Thanks for for your detailed help, in spite of the inaccuracy of the question.

The computer is currently running Ubuntu 8.10 and the 2nd hard drive is to add extra storage space, not to install Ubuntu. More exactly, this 2nd drive will be used to hold the files of virtual machines (VirtualBox 2.14) as the experts from VirtualBox forum advised me to store the VMs files on another physical disk to reduce the racing conditions on disk I/O.

Please pardon me for novice questions, I still need some clarifications from the above explanation. It is related to **sudo mkdir /{where you want it}**

[COLOR="Red"]**Q1.**[/COLOR] Why is there a need to create a directory? In other words, why does fstab need a directory rather than something simple like "mount this new 2nd disk". For example, when I put a DVD or a flash USB drive, they are mounted automatically and appear on the desktop. I don't need to create any folder or edit fstab. Can the new 2nd hard drive be used in some similar fashion? It's not that I am afraid of following the instructions you supplied above, I just want to understand why this 2nd drive must be prepared differently than an external USB drive.

[COLOR="Red"]**Q2.**[/COLOR] Let's assume that I decide to go with **sudo mkdir /VirtualBoxVDI**. Because there is no drive designation in the mkdir syntax, how can Ubuntu know that I want to create the VirtualBoxVDI folder in the new hard drive rather than the existing one?

---

### Post by drs305 on 2009-02-18
Questions are always welcome. I still don't know if this is an external or internal device. Removable devices such as cd-roms, flash drives, etc are designed to be removable, so ubuntu by default automounts them in certain places in /media.  

Permanent hard drives are not designated that way, so you have to tell ubuntu where you want them mounted when the system is powered up. This is done in fstab. *Slim Odds* is correct that /media is for removable drives. However, the line is slowly being blurred (at least by me and others). Traditionally permanent drives were mounted in /mnt  The main point is that this is by convention and you can actually mount a device wherever you desire. I place them all in /media and the system doesn't care a bit. It's a matter of personal choice. (Note: devices placed in /media traditionally have appeared as icons on the Desktop).

For permanent drives, you need to specify a location in fstab because it will be mounted during the initial boot and the system will look in fstab to determine where to mount it, who owns it, what type of formatting it has, etc.

So choose and make a mount point (*any mount point*), make yourself the owner,  and put it in fstab. /VirtualBoxVDI will work fine if you don't want it in a subfolder of /mnt or /media.

You asked about how ubuntu knows which drive you are talking about. As you have seen, ubuntu doesn't deal with drives like windows does (A:, B:, C: ).
Everything is a folder (or filesystem) to ubuntu, and all folders are located somewhere in the system. An internal device is *mounted* onto a mount point (folder) according to fstab's instructions (or manual *mount* instructions and where the device actually is doesn't really matter. You will see it as a folder within ubuntu.

---

### Post by Slim Odds on 2009-02-18
> **UranUtan said:**
> 
Please pardon me for novice questions, I still need some clarifications from the above explanation. It is related to **sudo mkdir /{where you want it}**


Questions are what these forums are for.....

For a real example: Just a couple of days ago I added a 400G IDE drive to my system to use for backups.

I mounted it as /data

That's what I mean. You pick a place that you like and put it there.

---

### Post by UranUtan on 2009-02-19
> **Slim Odds said:**
> Questions are what these forums are for.....

For a real example: Just a couple of days ago I added a 400G IDE drive to my system to use for backups.

I mounted it as /data

That's what I mean. You pick a place that you like and put it there.

May be I don't understand the mount point idea at all. What I am confused is when you do sudo mkdir /data. This means create the folder data under the root. My Ubuntu already have a root before the 2nd internal IDE hard drive is added.

Just to prove the point, here is what I did on my current system (the 2nd hard drive is **not** assembled yet):
```
sudo mkdir /testFolder
```
And sure enough, it is created where I expect it to be: the testFolder is created exactly under the root.

Then if I add a 2nd hard drive and re-issue the same mkdir statement above. Now suddenly, Ubuntu creates /testFolder in the 2nd hard drive. How strange is that?!? What if I wanted to create the folder in my 1st hard drive where the root is located?

I am OK to reference physical drive by folder as oppose to the one letter convention used in Windows. But creating a new folder and not having the ability to tell Linux in which physical drive the new folder should be located, I find that very confusing (and surely I have missed something obvious) 

In the evil world of Windows. I don't let the system "guess" where the new folder should be created (mkdir C:\TestFolder or mkdir D:\TestFolder).

So to take your example **"I mounted it as /data"**

Why didn't Ububtu create the /data folder under the root of the previous drive?

---

### Post by Slim Odds on 2009-02-19
It's really simple. You mount the drive where you want it.

You don't have to mkdir twice.

Before I first mounted the drive I did:```
sudo mkdir /data
```

Then I mounted the drive.

Here is my entry in fstab:
```
# /dev/sdc1
UUID=1b9f4c7e-09f6-4e12-a4cf-0XXXXXXXXXX /data           ext3    relatime        0       2

```

So when I boot, I get the entire drive at /data

Nothing more to it.

---

