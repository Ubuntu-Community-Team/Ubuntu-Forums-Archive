---
title: "New Kubuntu User"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Misagh on 2005-04-09
Hi all, hope everyone is well.
I downloaded Kubuntu 5.04 today, as I have been meaning to learn how to use a linux system for a while now, and have heard a lot good things about it.
I was very impressed by how easy it is to install and set up, even though it was text based.
Anyhow, I just have a few tiny problems that I was hoping someone could help me out with.
I currently have Kubuntu up and running without any major problems.
I have 2 hard drives in my pc, my primary is an 80gig drive, which I have split into 2, 1 partition has winxp pro (NTFS) and the other has kubuntu on it. My secondary hdd is a blank and i formatted it with the FAT32 file system.
By going to the storage media folder in kubuntu, I can see each hdd and each partition, however, I can not view the files on my winxp partition or my spare FAT32 drive.
When I try, I get this message :
Could not mount device.
The reported error was:
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

Is there any way I can fix this so I can view the files?
I understand that I can only access the files on my NTFS partition as read only, however, I should be able to read+write to the FAT32 partition.

---

### Post by arDAWG on 2005-04-09
Try this:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by devil28 on 2005-04-09
did you try to look at your fstab in etc/fstab? it seems as if hda1 is not listed there. open the file as root and add a line for hda1 according to the other partition(s). that should do the trick. come back if you have questions.

---

