---
title: "ntfs to xfs"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Eggbanjo on 2006-09-11
Ive recently installed 2 versions of xbuntu one on a desktop and one on my fileserver, compeletly replacing winblows. However on my fileserver i have over 600gb of stuff i want to keep spread across 5 disks.
 I cleared out one partition and formatted it as Xfs, now i want to copy the info from the ntfs partitions and then paste it into the xfs partitions, formatting the ntfs as i go.
 However if i try and copy it, its read only. any help would be greatful recieved!

:-k

---

### Post by kidders on 2006-09-11
Hi there,

You mean the XFS partition is read-only, or the NTFS one?

Assuming you mean the XFS one, doing your copy as root should sidestep any permissions difficulties you might be having. You can always set some more sensible permissions later.

Incidentally, do you have a UPS? Afaik the use of XFS without one is very dangerous ... it's hugely RAM-intensive, so it reacts rather badly to sudden power loss!

---

### Post by Eggbanjo on 2006-09-11
yeah i read about XFS and power surges, im all UPS'd up, so not to worried about that.

i can read from NTFS partition but cant copy from it, how do i copy as root, as all my attempts so far have failed, i tried sudo cp but that didnt work!

---

### Post by kidders on 2006-09-11
Glad to hear your power situation is sensible :-)

Unfortunately, it doesn't make sense to say that you can read something but not copy it, since copying *is* reading. Most likely, you're just having trouble writing to the destination. What error messages do you receive?

---

### Post by Eggbanjo on 2006-09-11
'omitting directory /media/Music'

thats with the command

sudo cp /media/Music /media/2/

---

### Post by Ramses de Norre on 2006-09-11
This will do: ```
sudo cp **-R** /media/Music /media/2/
```
cp doesn't include subdirectories by default, the R(ecursive) option will trigger this.

---

### Post by Eggbanjo on 2006-09-12
worked a treat - thanks

---

