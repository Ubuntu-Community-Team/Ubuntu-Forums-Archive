---
title: "Need help increasing size of root partition"
date: 2008-12-11
forum: General Help
---

### Post by Zevin64 on 2008-12-11
Hi, I'm a newbie to Ubuntu. I'm trying to increase the size of my root partition (6GB currently) so I can install more programs. However, when I boot from Ubuntu live CD and use partition editor I can't see my root partition, it should be a part of /dev/sda2 highlighted in the screenshot below:

[[IMG]http://img370.imageshack.us/img370/3867/screenshotnh9.th.png[/IMG]](http://img370.imageshack.us/my.php?image=screenshotnh9.png)

Some assistance please?

---

### Post by ajcham on 2008-12-11
I'm not sure what I'm missing here - your root partition appears to be sda1.  Could you right click on sda1 and select 'information', and this will show you the mount point of the partition.

EDIT: I've just spotted that all your partitions are NTFS partitions.  Can I ask how you've installed Ubuntu?  Did you use Wubi?

---

### Post by caljohnsmith on 2008-12-11
If you installed Ubuntu inside of Windows, I believe you can use LVPM to resize it:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by Zevin64 on 2008-12-11
the 6B partition is part of my Sony Vaio recovery.

Yes I installed Ubuntu inside of Windows, I'll try LVPM.

---

### Post by ramaswamyps on 2008-12-11
under windows the partition is not there for ubuntu.
it uses the available space in the windows partition.
you cannot increase the size for ubuntu only.
then you can increase size of the whole windows partition to get more space for ubuntu.
the sixe used by ubuntu inside windows is automatic allocated.

---

### Post by Zevin64 on 2008-12-12
> **caljohnsmith said:**
> If you installed Ubuntu inside of Windows, I believe you can use LVPM to resize it:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Thank you, that worked perfectly.:D

---

### Post by caljohnsmith on 2008-12-12
Glad to hear LVPM did the trick; cheers and have fun with your Ubuntu install. :)

---

