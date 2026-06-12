---
title: "Encoding problem reading windows partitions"
date: 2006-02-09
forum: Desktop Environments
---

### Post by jesusrop on 2006-02-09
I've installed Ubuntu in Catalan, and I have some problems reading windows partitions.

I used SuSE before, and I didn't have any problem, but now with Ubuntu, I can't read special characters, such as 'ú'. I know SuSE specified that to read those partitions, i had to use utf-8 locales, but I can't remeber how was it writen in '/etc/fstab'. Does anybody know how to specify utf-8 encoding for reading a partition in /etc/fstab???

(p.s.: I've tried the Ubuntu quick guide, and 'umask=000' and 'umask=0002' don't work!!! I need UTF-8 encoding only!!!)

---

### Post by jesusrop on 2006-02-09
Problem solved!!

The key word was iocharset, so adding iocharset=utf8 to the options in /etc/fstab solved the problem (if anyone else has this problem, doesn't need to ask)

Now anotherthing for wich I don't think I'm going to find the solution myself.

Is there any way of changing the names displayed for mi drives??
When browsing my computer, I see "hda1" and things like this, wich is good for me, but my parents don't understand...

How can I diplay customized names, like "Documents" or "Windows"???

---

### Post by Sutekh on 2006-02-09
What sort of partition has the special characters, ext3 or FAT or NTFS or what? 

**umask** is the flag to allow permissions to the partition.  If the partition is ext3, you don't need umask at all.  If FAT you want umask=0000.  If NTFS you want umask=0222.  But it doesn't have an effect on reading special characters.


You should try adding this to the entry after specifying the filsystem type;

For ext3:
I don't know if you can or need to.

For FAT:
```
iocharset=utf8
```

For NTFS:
```
nls=utf8
```

Wow, you solved it yourself and I didn't even check.

---

### Post by jesusrop on 2006-02-10
Curiously I don't have this problem with NTFS...only with FAT partitions

Thanks for your time!

---

