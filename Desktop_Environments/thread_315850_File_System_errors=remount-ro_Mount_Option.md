---
title: "File System errors=remount-ro Mount Option"
date: 2006-12-09
forum: Desktop Environments
---

### Post by TerryHowe on 2006-12-09
What does the errors=remount-ro option do on the file system do?  I'm having a problem where my root file system is becoming read only and somethings get I/O errors.

/dev/hda1 on / type ext3 (rw,errors=remount-ro)

---

### Post by lukew on 2006-12-21
> **TerryHowe said:**
> What does the errors=remount-ro option do on the file system do?  I'm having a problem where my root file system is becoming read only and somethings get I/O errors.

/dev/hda1 on / type ext3 (rw,errors=remount-ro)

Hi, 

It remounts the parition when errors occur as readonly.

You have problems with your hd. You need to run fsck to correct errors.

If you can change the mount option to:

[HTML]errors=continue  [/HTML]

to allow you to carry on, but i would only do this if you you cant continue with the state of your system and can not fix it!!!

I hope this helps.
Luke

---

