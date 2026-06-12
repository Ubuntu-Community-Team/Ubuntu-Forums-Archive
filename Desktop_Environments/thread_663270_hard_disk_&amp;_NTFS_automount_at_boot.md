---
title: "hard disk &amp; NTFS automount at boot"
date: 2008-01-09
forum: Desktop Environments
---

### Post by yourjune on 2008-01-09
I have been used Ubuntu gusty desktop and it's been very well with out any trouble. I have three ntfs partitions and one of them is actual independent hard drive. Those are all well appeared on my desk top after boot process done.  One day I have unmounted my ntfs partition and next time when logged in, I couldn't find any of them.
So I tried to mount one of them using strings which I have got here and there on the web.
Nothing works.

Is there any easy way to restore the original settings. Many of stuffs appointed that the file fstab in /etc should be modified for ntfs auto-mount at boot but ... there should be easy gui package for this kind of settings properly.

Please help!!

---

### Post by Emerzen on 2008-01-09
Try this:

go to Applications-->Add/Remove

type "ntfs" in the search bar.  (make sure "show all available software is selected.")

Install the program that pops up...ntfs-configuration

Once installed, go to Applications-->System tools -->Ntfs-config

A window will open and check off "enable read/write support for internal and external drives" ...your ntfs partitions should pop up.

---

### Post by yourjune on 2008-01-10
Thanks! Emerzen

It works fine for me.

---

### Post by Niniel on 2008-01-11
Excellent, thank you.

---

### Post by Emerzen on 2008-01-11
Glad it worked!

---

