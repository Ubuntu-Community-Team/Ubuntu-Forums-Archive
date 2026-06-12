---
title: "dd doesn't copy, says /media/cdrom0 is a directory"
date: 2009-04-18
forum: General Help
---

### Post by chimmie on 2009-04-18
I can't get dd to work on anything other than a simple file.

jim@ubuntu-basement:~$ dd if=/media/cdrom0 of=image.iso
dd: reading `/media/cdrom0': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000564457 s, 0.0 kB/s
jim@ubuntu-basement:~$ 

I get this even when trying to copy a directory from my system:

jim@ubuntu-basement:~$ dd if=/sys of=sysimage.iso
dd: reading `/sys': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000573467 s, 0.0 kB/s
jim@ubuntu-basement:~$ 

What am I doing wrong?

I have also tried running the command as sudo dd....   same results.

---

### Post by dcstar on 2009-04-18
> **chimmie said:**
> I can't get dd to work on anything other than a simple file.

jim@ubuntu-basement:~$ dd if=/media/cdrom0 of=image.iso
dd: reading `/media/cdrom0': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000564457 s, 0.0 kB/s
jim@ubuntu-basement:~$ 

I get this even when trying to copy a directory from my system:

jim@ubuntu-basement:~$ dd if=/sys of=sysimage.iso
dd: reading `/sys': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000573467 s, 0.0 kB/s
jim@ubuntu-basement:~$ 

What am I doing wrong?

I have also tried running the command as sudo dd....   same results.

dd copies from files or file-like devices, not filesystems.

If you want to copy from a CD/DVD, you must specify the /dev/sd device, not the filesystem mount point.

---

### Post by ad_267 on 2009-04-18
Try /dev/scd0 instead of /media/cdrom0

/dev/scd0 is the actual device, /media/cdrom0 is where it is mounted.
Also run the "mount" command to check that your cdrom device is actually /dev/scd0 and not something else.

---

### Post by chimmie on 2009-04-19
Thank you. That's exactly the info I needed.  -Chimmie

---

