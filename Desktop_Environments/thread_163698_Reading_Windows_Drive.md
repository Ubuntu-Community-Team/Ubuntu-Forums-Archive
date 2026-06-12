---
title: "Reading Windows Drive?"
date: 2006-04-21
forum: Desktop Environments
---

### Post by greghill on 2006-04-21
I recently had to do a complete reinstall of Ubuntu (Power failure corrupted Drive). On my previous installation, I remember installing or running a script that would allow me access to my other hard drive (hda) where Windows is installed, bu I can't seem to find it anywhere (spent hours looking). If anyone has this, could you post it again, or email it to me? Thanks in advance.... I know I can count on you all for help!!
Greg

---

### Post by taurus on 2006-04-21
You are talking about modifying your /etc/fstab so your Windows will mount automatically upon boot with read access to everybody.  Here is what you do from a terminal...
```

sudo mkdir /Windows  <-- to create a mount point
sudo nano /etc/fstab  <-- to edit it

```
Now, use the arrow key and scroll down to the bottom of the screen and add the following line to it.  Then save it with <Ctrl> and x and then y...
```

/dev/hda1  /Windows  ntfs  defaults,umask=02222  0  0
(assuming that Windows is on /dev/hda1 and the file system is NTFS...)

```
Now, mount it with
```

sudo mount -a

```

---

### Post by greghill on 2006-04-21
This doesn't work. Complaining about wrong file type, or bad superblock. 
I don't remember having this problem before. It is Windows XP and AFAIK  the file system is ntfs. I do remember typing in unmask=220, but not unmask =222 0 0 . Don't get me wrong...I'm not a programmer in any way, shape or form.... it just doesn't look familiar to me... so I'm asking... is this right?
The directory was created as directed (verified), but when I try to mount it, it just complains as above. Can I try something else?  Again, thanks for your help.
Greg

---

### Post by greghill on 2006-04-21
Taurus - just in case you caught the typo in my last post, it says  unmask=2222 0 0  and it should have read unmask=02222 0 0 .
What a difference one digit makes. Unfortunately, it didn't make any difference in the way the system responded. Still complains of bad fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error.

---

### Post by greghill on 2006-04-23
Just an update - I finally got it working. Seems all I had to do was leave off the 0 0 from unmask=02222 0 0 . Thanks for your help, Taurus!
Greg

---

