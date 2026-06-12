---
title: "Need help with permission after formatting NTFS volume"
date: 2006-08-27
forum: Desktop Environments
---

### Post by pseudoanon on 2006-08-27
I have an extra drive on my system, independent of either XP or Ubuntu (which reside in different partitions on another drive). I was planning to use it to store misc. media and what not. Unfortunately, after successfully formatting it to ext3 and mounting it, I can't find a way to edit the permissions to allow me to write to this volume. I've made some token forays into chmod and fstab, but to no avail. Any help would be greatly appreciated.

---

### Post by taurus on 2006-08-27
If it's a ext3 filesystem, then you can use chmod to set permissions to it...

```
sudo chmod 777 /media/harddrive
```

---

### Post by aysiu on 2006-08-27
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by pseudoanon on 2006-08-27
Thank you, taurus. That was all I needed. Now if only I could understand how I did that. :)

---

