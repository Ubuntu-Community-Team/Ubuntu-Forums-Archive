---
title: "Is it worth trying out ext4?"
date: 2009-06-15
forum: General Help
---

### Post by Macfunky on 2009-06-15
Im going to be installing Jaunty onto a computer later on today. I have heard great things about ext4 such as its like an upgrade in hardware. Is it really this good? Also is it worth it cause i have also read its not fully stable yet and there is a risk of data loss. This computer isnt gonna be used for anything important anyway but i would prefer if strange things didnt happen. Anyone have any problems with ext4? If so what? And would you recommend it?

---

### Post by ActiveFrost on 2009-06-15
Fedora 11 uses ext4, so .. I wouldn't say it's unstable.

---

### Post by Legace on 2009-06-15
> **Macfunky said:**
> Im going to be installing Jaunty onto a computer later on today. I have heard great things about ext4 such as its like an upgrade in hardware. Is it really this good? Also is it worth it cause i have also read its not fully stable yet and there is a risk of data loss. This computer isnt gonna be used for anything important anyway but i would prefer if strange things didnt happen. Anyone have any problems with ext4? If so what? And would you recommend it?

I've used EXT4 with Jaunty 64-bit for quite a while now and I have to say that the machine seems a little faster now.. I haven't suffered from any problems, and I doubt you will, either. Give it a go :)

Check this out: [http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=2](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=2)

---

### Post by ultratwo on 2009-06-15
I haven't had any problems with it. It's marked as stable in the kernel.


EDIT: This only applies if certain features are enabled (I don't think they are in ubuntu). Note that ext4 cannot be read by previous versions of Ubuntu and any Linux with a kernel older than 2.6.28 (released on Oct 11'th 2008), though an unstable version has been in the kernel for longer than that

---

### Post by Gen2ly on 2009-06-15
Using it too and like it.  No problems for... 4 months.

---

### Post by Soul-Sing on 2009-06-15
No problems here with ext-4

---

### Post by rizman on 2009-06-15
I had my home partition formatted to ext4 under jaunty and haven't had any problem with it. But, for some reasons (ATI card which has been put on legacy support) I switched back to Hardy Heron. That caused some major troubles because I had to reformat to ext3. It took me the whole weekend to backup, re-install, restore with some Grub issues in the middle of the way. But finally everything is OK.

So if you don't plan to revert back to an older version of Ubuntu, I'd say go with ext4.

---

### Post by lovinglinux on 2009-06-15
No problems here. 

There are already a few discussions about ext4 in the forums:

[Ext3 and Ext4: Which file system to install?](http://ubuntuforums.org/showthread.php?t=1133719)
[have you had any problems with ext4?](http://ubuntuforums.org/showthread.php?t=1170802)
[Should I switch to ext4?](http://wwww.ubuntuforums.org/showthread.php?t=1157658)
[Is EXT4 safe?](http://ubuntuforums.org/showthread.php?p=7423993) 
[Choosing ext4 over ext3](http://ubuntuforums.org/showthread.php?p=7209536)
[Jaunty and EXT4](http://ubuntuforums.org/showthread.php?t=1180097)

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=ext4+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) | [Forum Search](http://ubuntuforums.org/search.php?do=process&query=ext4)

---

### Post by The-ITu on 2009-06-15
isent ext for Wubi?

---

### Post by ActiveFrost on 2009-06-15
> **The-ITu said:**
> isent ext for Wubi?

Umm ? Ext3/Ext4 are filesystems - the same as FAT32 and NTFS for Win32 machines .. you can't get rid of it :p

---

### Post by HavocXphere on 2009-06-15
Use it, but be on top of things with your backups.

And sync'ing doesn't count. It would just overwrite your backups with zero files.

If you use the PC to put food on the table then stay with ext3.

---

