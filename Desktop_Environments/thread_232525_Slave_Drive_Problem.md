---
title: "Slave Drive Problem"
date: 2006-08-08
forum: Desktop Environments
---

### Post by stevetheman on 2006-08-08
Even though this problem won't make a lot of sense because this is a windows machine, I have an ubuntu Live CD and the partition that I need to fix is FAT32 so I thought that maybe the Ubuntu community could help, because the Windows side of things haven't been very promising. This drive has a corrupt boot sector and also a corrupt MBR. I need to fix these two parts of the drive using freeware programs and also I need to salvage the data. What can I do? Ubuntu won't mount the drive when it starts and neither will windows.

---

### Post by catlett on 2006-08-08
You'll have to manually mount the partition. First you need to know what partition it is on. Open the terminal (it's under Applications<Accessories<Terminal) and enter```
 sudo fdisk -l
```
Once you know the partition, you have to make a place to mount it and then mount it. You can put it in fat32 undser media. Do this but replace the partition with the fdisk output for your fat32 partition.
```
sudo mkdir /media/fat32
```
```
sudo mount /dev/hda2 -t vfat /media/fat32
```
I am just guessing at /dev/hda2. Use the actual label from sudo fdisk -l for the fat32 partition. If you can't figure it out, post and I'll tell you.
If it doesn't appear as an icon on the desktop then go to the top panel and enter Places<Computer<Filesystem<Media and there will be a fat32 folder.

If you have a problem, just post

---

### Post by stevetheman on 2006-08-08
I don't need to get it to mount in Ubunutu. I want to fix the drive by repairing the Boot Sector and the MBR and was wondering if there is a way to do this in either Linux or a Linux App.

---

### Post by computergroove on 2006-08-08
Your best plan of action is to get the data off the hard drive asap. I work with hard drives that do this all the time. There is a better chance that the drive is going bad then the MBR being corrupt. What version of windows is installed on the drive? Do you have an install cd for that version available? I use Winternals ERD commander (not exactly free) to retrieve data before I attempt a repair of a hard drive because you can permantly damage the data if something goes wrong. Any idea how the MBR go damaged? You can use freeware programs provided by the manufacturer of the hard drive if they offer them (most do). Seagate tools offers a universal tool for hard drive testing. I think you will want to use the software specifically for that hard drive though because you will sometimes get the option of repairing the MBR.

---

### Post by stevetheman on 2006-08-09
I need a tool that can copy the almost-lost data of the slave drive to a spot on the primary drive. Is that what the Winternals program will do? Where do I get a copy and how is it "not exactly free"?

---

