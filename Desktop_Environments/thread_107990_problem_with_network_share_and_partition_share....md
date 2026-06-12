---
title: "problem with network share and partition share..."
date: 2005-12-24
forum: Desktop Environments
---

### Post by shaj on 2005-12-24
hey hope you guys can help...

a few problems...

-Problem 1

I've added the comment

'/dev/hda1       /home/shaj/MyWin	ntfs    nls=utf8,umask=0222 0       0'

in my fstab file to mount my windows partition on startup.

a) it doesn't seem to automatically mount on startup. I have to manually go to system->admin->disks and press enable on that partition.

b) even after enabling, it doesn't show up on the desktop like it used to before.

-Problem 2

For some reason, all of a sudden, when I go to 'network servers' it asks me for login n password??? This never used to happen before. I leave the name n pass blank and it does login, but this never used to happen before?


Hope you guys can help me with these problems...

---

### Post by kaamos on 2005-12-24
You should create a folder in /media
```
sudo mkdir /media/MyWin
```
And then change the fstab line to
> /dev/hda1       /media/MyWin  ntfs    nls=utf8,umask=0222 0       0
Only mounts in /media show up on the desktop.

---

### Post by shaj on 2005-12-24
[QUOTE=kaamos]You should create a folder in /media
```
sudo mkdir /media/MyWin
```
And then change the fstab line to

Only mounts in /media show up on the desktop.[/QUOTE]


oooooooops. thanks so much!!!!

any idea about the login problem?

also another question. I have a folder on the windows network called

'Storage (I)'

How do I mount that?

---

### Post by kaamos on 2005-12-24
No prob. :)

I think this should get the second problem fixed [http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)

---

