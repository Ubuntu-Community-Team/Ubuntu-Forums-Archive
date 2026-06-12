---
title: "Where's my second drive?"
date: 2009-05-23
forum: General Help
---

### Post by Mikethebook on 2009-05-23
I'm a complete Ubuntu Linux novice. Not a clue!! I've just installed it on my wife's computer fed up with it repeatedly crashing on Windows 2000 and decided to give it a try. So far so good. But I can't find her second internal drive the D drive on which she keeps all her personal files. Can anyone help please?

---

### Post by drs305 on 2009-05-23
First, welcome to the ubuntu forums.

We need to know a bit about your system. Do you know the format of the drive (partition) you are trying to mount? You can find out by opening a terminal (Applications, Accessories, Terminal) and typing:
```
sudo fdisk -l
```
That is a lowercase L.

It is possible the drive is already mounted. You can run this command to see what drives/partitions are mounted and where:
```
mount
```
Normally the partitions, if automatically set up, will place the drive in either /media or /mnt. Use your file browser to explore the addresses found by the "mount" command if you see your device listed.

If it is an NTFS formatted drive, you can't find it, and you want to keep it as NTFS, the easiest way to set it up is to use the NTFS configuration tool. The following link has good instructions - go to the Configuration section.
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

If you aren't sure what you have, just post the results of the "fdisk" command above. Since the device has to be mounted, you could also tell us the name of the folder you want to mount it in (like "mydata", "music", etc). You also have to decide what type of format you want to use, such as native Linux (ext3 or ext4), NTFS (windows), or some other like FAT32.

---

### Post by DeMus on 2009-05-23
> **Mikethebook said:**
> I'm a complete Ubuntu Linux novice. Not a clue!! I've just installed it on my wife's computer fed up with it repeatedly crashing on Windows 2000 and decided to give it a try. So far so good. But I can't find her second internal drive the D drive on which she keeps all her personal files. Can anyone help please?

Use this:

**_Auto mount Windows disks_**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by Woody1987 on 2009-05-23
try clicking on the places menu at the top and it should appear on the list.

---

### Post by Mikethebook on 2009-05-24
Hi Everyone. Thanks for your help. I find this very scary going back to something like DOS and I never understood that. It's temting to go back to the user friendliness of Windows but I don't want to give up just yet. drs305, I did want you said but couldn't understand all the text. Demus, want you suggested makes some sense but I haven't tried it yet. I have two questions. Will the NFTS config tool wipe out everything on the D drive or just reconfigure it. Will you also explain mounted and unmounted especially as how that relates to Windows. Under Computer I can only find the normal C drive with Ubuntu on, USB drives with nothing there and the CDRom drive. There is nothing showing on the desktop as such. Can i go and automount the D drive? Thanks for your help. If I can get this to work then I'll probably persevere with Ubuntu.

---

### Post by drs305 on 2009-05-24
The good news is that mounting/unmounting does not do anything to your data other than to make it available to the system (or not). It doesn't alter the data. 

Here is the ubuntu wiki link on mounting. It probably will explain things better than what I write below:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

There are a couple of concepts that should help you understand linux file mounting. 
1. Generally speaking, linux considers everything a file. Sometimes it's easier for a windows user to think of it as a folder. To be accessible, everything must be mounted in a folder before linux can see and use it. You place the contents of the partition you want to view into a specific folder by by mounting it. You can do this manually via a terminal command or perhaps by clicking on the device icon in your file browser or on your desktop. It can be done automatically by the system and by reading the contents of /etc/fstab, the file which gives the system instructions on where to mount the devices.

2. Notice I don't use the term "drive", but "partition". Linux doesn't read a drive, but its partitions. It doesn't read Drive D in its entirety, but rather the individual partitions (devices) on Drive D. They are designated as sd**XX**, with XX being the drive letter (a,b,c,d, etc) and the partition number (1,2,3, etc). So your D drive's first partition will show up as sdX1, probably sdb1. Notice that as a windows user you think of Drive D, but the letter in linux can be any letter - don't look for just "d". Generally, the first drive linux finds is "a", the second "b", etc. 
3. To mount a device (partition), linux needs to know 3 things. It needs the device name (sdXX). It requires a mount point (where to mount it). The mount point is usually a subfolder of /media or /mnt, which you must create before attempting to mount. Finally the system needs to know the type of formatting the device uses (ext3, ext4, NTFS, fat32, etc.

You can see what devices linux has found and mounted by running this command:
```
mount
```
To limit the output, you can run this:
```
mount | grep "/dev/sd"
```
Do you see your D drive partitions listed?

Running the following command should show all the devices the machine can find.
```
sudo fdisk -l
```
If the system recognizes your D drive, you should see an output that includes a line similar to this. The sd**XX** designation will be different.
> /dev/sdb1  38660   38709  401593+  7  HPFS/NTFS

If your D drive partitions show up with this command, you should be able to mount them without too much difficulty.

Check your forum inbox, I've sent you a PM.

---

