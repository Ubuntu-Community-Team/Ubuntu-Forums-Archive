---
title: "Ubuntu/XP dual boot"
date: 2009-05-10
forum: General Help
---

### Post by d42 on 2009-05-10
Not exactly ubuntu related, but I hope someone can help.

I set up a ubuntu/XP dual boot, so I can run games on XP and do everything else on ubuntu.

Ubuntu was installed first, then XP. The problem is that the XP local drive is the J drive, but windows is still trying to install things to C (listed as a removable drive).

Anybody heard of this problem before?


Edit: [http://support.microsoft.com/kb/307844](http://support.microsoft.com/kb/307844) seems to have something to say on this. Would switching drive letters effect ubuntu?

---

### Post by x22 on 2009-05-10
> ubuntu first...then XP

sorry, wrong order: dualbooting with M$ OSs the rule is, 
install the M$ OS first.  Let it have the whole disk

then use gparted to cut the M$ partition back: 10GB, or 
whatever you think is enough: *then* install another OS 
onto the unused unpartitioned space.

---

### Post by BslBryan on 2009-05-10
Hello, d42. :-)

Switching drive letters on a Windows operating system will not interfere with Ubuntu, as far as I know.  

Best to you, and good luck.

---

### Post by bumanie on 2009-05-10
Post the output of > sudo fdisk -l to show the drive/partition setup of your computer. This can be done via live ubuntu cd or from within ubuntu.

---

