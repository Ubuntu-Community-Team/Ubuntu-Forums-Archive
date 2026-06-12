---
title: "Unmounting Partitions?"
date: 2006-01-17
forum: General Help
---

### Post by Im_Just_GrayT on 2006-01-17
Ive just recently installed breezy on my computer dual booted with winXP. 

when i use system>admin>disks to mount my windows partition (and my file partition) it works fine. but when i reboot my computer i have to remount my partitions again:confused: . am i doing anything wrong?

also how can i change the permissions to these partitions so i dont have to be root to write to them? Thanks:smile:

---

### Post by lamego on 2006-01-17
[QUOTE=Im_Just_GrayT]Ive just recently installed breezy on my computer dual booted with winXP. 

when i use system>admin>disks to mount my windows partition (and my file partition) it works fine. but when i reboot my computer i have to remount my partitions again:confused: . am i doing anything wrong?

also how can i change the permissions to these partitions so i dont have to be root to write to them? Thanks:smile:[/QUOTE]

The paritions mounts table is /etc/fstab :
sudo gedit /etc/fstab
Here are my mounts just as an example:
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0

---

### Post by mark_g on 2006-01-17
You need to put it in the fstab file, so it is mounted automatically at startup. You can read how in the ubuntuguide:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

If you have more questions, just ask.

---

### Post by o_fortuna on 2006-01-17
[QUOTE=Im_Just_GrayT]Ive just recently installed breezy on my computer dual booted with winXP. 

when i use system>admin>disks to mount my windows partition (and my file partition) it works fine. but when i reboot my computer i have to remount my partitions again:confused: . am i doing anything wrong?

also how can i change the permissions to these partitions so i dont have to be root to write to them? Thanks:smile:[/QUOTE]
You should restart your computer first (so that Windows isn't mounted anymore), then, to permanently mount a windows XP partition (I assume NTFS), type
```
mkdir /media/windows
sudo gedit /etc/fstab 
```
Add this line to the bottom of the file
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```
Save and exit the program, then copy one final thing into the terminal to mount windows:
```
mount -a
```
An icon should appear on the desktop. You're done!

As far as writing to NTFS, it's generally not recommended. Read [this]("https://wiki.ubuntu.com/NTFSReadWrite?highlight=%28ntfs%29") for more information.

---

