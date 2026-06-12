---
title: "Error removing file: Read-only file system"
date: 2009-01-22
forum: General Help
---

### Post by equal on 2009-01-22
I just made a total newbie mistake here. I was loading some files onto an Micro SD card, and I yanked it out of my card reader without unmounting the card first. Now all the files have a  padlock symbol on the icon, and I can't even delete them from my memory card because I get an error saying "Error removing file: Read-only file system". I can't modify the file permissions either, because I get "Error setting permissions: Read-only file system"

I haven't messed around with files like this in ages, can someone remind me how to fix this problem?

---

### Post by Julius1988 on 2009-01-22
what happens when u try "sudo chmod -R 755 <folder-name>" on the folder were the card is mounted.

---

### Post by equal on 2009-01-22
> chmod: changing permissions of `/media/disk/Zelda - Phantom Hourglass.sav': Read-only file system

Still doesn't work :(

---

### Post by equal on 2009-01-22
oops double-posted my reply

---

### Post by amac777 on 2009-01-22
Try remounting the disk as writable:

```
sudo mount -o remount,rw /media/disk
```

And then accessing the files.

---

### Post by Captain Giraffe on 2009-01-22
A guess is that the filesystem is marked as dirty and must be checked before you can use it again.
If I recall correctly fsck is the command to use.
You have to unmount the drive before you run it. I'm sure google is your friend here with exact commands. 
/Cpt.G

---

### Post by equal on 2009-01-22
**amac777**: That worked! Thanks so much!

---

### Post by Arphitz on 2009-05-19
I still got the same problem hear...
command that 777 gave doesnt work with me...
now i cannot delete my pendrive data...
somebody help me...
:(

---

### Post by amac777 on 2009-05-19
Arphitz, you probably need to provide more details (also normally it's a good idea to start a new thread for a new question).

Can you tell us the directory where your pen drive is being mounted?

Also, what is the output of this command:

```
mount
```

Also, what is the exact error message you see when you try to delete a file from the USB disk?

---

### Post by Dex73 on 2009-05-20
My Micro SD to SD card used to plug my micro SD into regular SD slot has a slider that looks like a lock in the card mechanism but is actually a read only switch similar to those on a floppy. Can't manipulate anything when in the wrong position. Could this be the problem?

---

### Post by formol on 2009-07-25
I tryed to remount with rw, here is was I got:

> mount: block device /dev/sdd1 is write-protected, mounting read-only

I just don't know what happen, this drive was working really well 20 minutes ago, it unmounted alone and became "write-protected" by itself.  does someone know was to do with this?

---

### Post by amac777 on 2009-07-25
Did you check what Dex73 suggested above? (check the little physical switch on the side of the SD card to see if you have it set in the write-protect position.)

---

### Post by formol on 2009-07-25
No, it's not a sd card but a 500gb ide disk. 

In fact, this disk begun to act strangely after a sudden electrical failure during a storm. It took 3-4 reboot before the disk reappear, I don't know why.  
Since I got problem whit this drive (the 3 other sata drive are very functionnal). When I use to copy from this disk to another, my computer freeze and reboot, after variable time. Or sometime, again after reboot, all the file are locker as "system file". 

So if someone could explain me this situation, I would appreciate :)

(I will try this weird disk in another computer when I'll be back here later today, maybe it'll work...)

---

### Post by amac777 on 2009-07-25
Well, it could be a hardware problem if the drive got zapped during the storm....

But it could also be that the sudden shutdown during the storm caused errors on the drive so now each time it mounts it will be read only.

I would suggest checking the disk for errors using fsck. You need to un-mount the disk before you can check it. So assuming the drive is /dev/sdb1, try running these commands:

```
sudo umount /dev/sdb1
sudo fsck /dev/sdb1
```

If fsck finds errors, it will probably ask you if you'd like it to attempt to fix them. If think that is the default behavior. Otherwise you can run it as 'sudo fsck -r /dev/sdb1' to ask it to interactively repair any errors it finds.

Assuming fsck finds and fixes some errors, the disk might start working normally again afterwards.

---

### Post by Drahreg13 on 2010-06-16
try
sudo chmod 777 /etc/fstab

dosfsck -a /dev/(your device)

dosfsck -r /dev/(your device)

mount -o rw,remount /path/to/your/device

> **equal said:**
> I just made a total newbie mistake here. I was loading some files onto an Micro SD card, and I yanked it out of my card reader without unmounting the card first. Now all the files have a  padlock symbol on the icon, and I can't even delete them from my memory card because I get an error saying "Error removing file: Read-only file system". I can't modify the file permissions either, because I get "Error setting permissions: Read-only file system"

I haven't messed around with files like this in ages, can someone remind me how to fix this problem?

---

### Post by kari-kun on 2010-06-17
> **amac777 said:**
> Did you check what Dex73 suggested above? (check the little physical switch on the side of the SD card to see if you have it set in the write-protect position.)
WOW!
I feel so stupid! That was the problem with mine after all, thanks so much!

---

