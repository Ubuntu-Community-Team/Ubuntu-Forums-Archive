---
title: "Read access to Win files - Dual Boot"
date: 2006-01-03
forum: General Help
---

### Post by orsula on 2006-01-03
Hi,

I recently installed Ubuntu 5.10 on a box with WInXPro. Dual boot works flawlessly with grub. HOwever, on my desktop I have an icon for hda1 which is supposed to be the Win partition. When I try to access it I get the folowing message:

"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "hda1"."

How can I have read permission to the files on my window partition? Do I need to mount it somehow to /mnt?

thanks.

Gidi

---

### Post by darth_vector on 2006-01-03
open /etc/fstab as root:
```
sudo gedit /etc/fstab
```
and look at the line that corresponds to hda1. it should look something like this
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```


have a read of the "How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only" section of the ubuntu guide:

 [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

---

### Post by orsula on 2006-01-03
[QUOTE=darth_vector]open /etc/fstab as root:
```
sudo gedit /etc/fstab
```
and look at the line that corresponds to hda1. it should look something like this
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```


have a read of the "How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only" section of the ubuntu guide:

 [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)[/QUOTE]


Hi:
This is the line corresponding to hda1:
/dev/hda1       /media/hda1     ntfs    defaults        0       0

thanks for the reference though.

---

### Post by carlosqueso on 2006-01-03
just replace "defaults" with "umask=0222".  Then open a terminal and type ```
sudo umount /media/hda1
mount -a
``` and it should work.

---

### Post by orsula on 2006-01-03
I went through the motions in the above link. I still get 

"You do not have the permissions necessary to view the contents of "hda1"."

Is there somewhere else to set the permissions?
My /etc/fstab for hda1 is the following:

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

thanks
Gidi

---

### Post by orsula on 2006-01-03
ok - I don't get the error regarding permission, but I can't see any files on my WinXp partition. Can Ubuntu handle viewing ntfs files?

---

### Post by Omnios on 2006-01-03
This is a link to the Unofficial Ubuntu starters guide with mount info for both manual and automount just scroll down a bit for automounts

[http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

---

### Post by orsula on 2006-01-03
nevermind - I can see it all.

Thank you very much for the quick replies. It helps a lot for a newbie such as me..;)

---

