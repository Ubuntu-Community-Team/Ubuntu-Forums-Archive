---
title: "dmg"
date: 2009-04-19
forum: General Help
---

### Post by db21 on 2009-04-19
It's maybe in the wrong section and a noob question.
I just want to if it's possible to download a dmg file which have a size more than 4gig.

thanks!

---

### Post by lvleph on 2009-04-19
Why wouldn't it be possible to download a dmg larger than 4GB. Maybe I don't understand your question. If you need to know how to mount it:
[http://ubuntuforums.org/showthread.php?t=125526](http://ubuntuforums.org/showthread.php?t=125526)

---

### Post by db21 on 2009-04-19
because when i try to download on my windows and the file is like 5gig, it wont download (idk why) but under 4gig i dont get any problem. 

I ask that before i decide to switch to ubuntu.

---

### Post by ukblacknight on 2009-05-03
If you're installing on ext3 filesystem (most likely, it's the default), you can have files upto 16GB in size.  ext4, which is an option in the Ubuntu 9.04 installer allows upto 16TB.  So to answer your question, yes :P

NTFS used to have a limitation of 4GB - I'm not so sure if this is true anymore.

---

### Post by 3rdalbum on 2009-05-03
Fat32 is one of the filesystem formats on Windows, and it doesn't support files bigger than 4 gigabytes. This is a limitation of the filesystem and it occurs when using a Fat32 filesystem on Linux, for instance if you are downloading a file directly to a flash drive.

---

### Post by Zoowey on 2009-05-03
> **3rdalbum said:**
> Fat32 is one of the filesystem formats on Windows, and it doesn't support files bigger than 4 gigabytes. This is a limitation of the filesystem and it occurs when using a Fat32 filesystem on Linux, for instance if you are downloading a file directly to a flash drive.

Most higher capacity flash drives can be formatted with NTFS therefore getting rid of Fat32's limitations.

---

### Post by Zoowey on 2009-05-03
> **ukblacknight said:**
> NTFS used to have a limitation of 4GB - I'm not so sure if this is true anymore.


Actually NTFS can support a file size of up to 1 extabyte which is essentially 1,048,576 terabytes or 1,073,741,824 gigabytes.

---

### Post by llemm on 2009-05-03
> **Zoowey said:**
> Actually NTFS can support a file size of up to 1 extabyte which is essentially 1,048,576 terabytes or 1,073,741,824 gigabytes.

According here [http://www.ntfs.com/ntfs_vs_fat.htm]("http://www.ntfs.com/ntfs_vs_fat.htm")

The NTFS can only support 2TB Volume. Old or Unpatched windows XP has also 4 GB limit. But the newest one is unlimited

---

### Post by happyhamster on 2009-05-03
Note that the maximum file size for ext3 depends on the file system's block size. With a default block size of 4 kB, you can get files up to 2TB. 

The only file I've seen that was bigger than 16Gb was a virtual disc image (Virtualbox with winXP installed IIRCC).

---

