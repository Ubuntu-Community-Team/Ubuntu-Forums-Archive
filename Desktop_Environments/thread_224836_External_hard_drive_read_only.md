---
title: "External hard drive read only"
date: 2006-07-28
forum: Desktop Environments
---

### Post by declaration on 2006-07-28
Hi,

I have an external hard drive which Ubuntu shows automatically.
However it is read-only and ubuntu won't let me change the permissions even as root,

There isnt even an entry in fstab for this drive.

How do I make it writeable?

Thanks

---

### Post by Jagot on 2006-07-28
What file system is the drive using?  If it's NTFS then it is only read-only as far as Ubuntu is concerned - Linux cannot write to NTFS partitions safely.

---

### Post by roostishaw on 2006-07-28
> **Jagot said:**
> What file system is the drive using?  If it's NTFS then it is only read-only as far as Ubuntu is concerned - Linux cannot write to NTFS partitions safely.
Key word, "safely". But it can be done.
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read%2Fwrite](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read%2Fwrite)
or
[http://lunapark6.com/?p=1710]("http://lunapark6.com/?p=1710")  (by following the instructions near the bottom, "ubuntu specific")

...all at your own risk.

---

