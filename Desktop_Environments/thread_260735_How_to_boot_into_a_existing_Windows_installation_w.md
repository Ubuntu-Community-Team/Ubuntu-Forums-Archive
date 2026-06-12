---
title: "How to boot into a existing Windows installation with VMWare?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by BoyBlunder on 2006-09-19
is this possible at all? I've tried searching the HOW TO forum but I'm coming up with nothing.

---

### Post by bswilson on 2006-09-19
> **BoyBlunder said:**
> is this possible at all? I've tried searching the HOW TO forum but I'm coming up with nothing.

If I understand your question correctly; no, it isn't possible.

I'm assuming you want to boot directly into a Windows image that you installed under VMware.  If that's what you mean, then the VMware application has to be running in order to boot Windows.  Obviously, you can't run VMware outside of the host OS, which means you can't boot directly into an image.

---

### Post by rhpot1991 on 2006-09-19
I think what he is trying to accomplish is to dual boot a computer, and use vmware while in linux to access his windows partition.  I have heard this is possible, but cannot tell you how to do so.  Good Luck.

---

### Post by BoyBlunder on 2006-09-19
Yea, right now, I've got a dual boot system, Ubuntu 6.06 & XP Pro. I'm looking to see if I can get my XP install to work under VMWare (or any other tool, really) successfully.

---

### Post by moore.bryan on 2006-09-19
*do you just want to access files on the ntfs xp partition or run windows?  the former is, relatively, easy; the latter, not at all.*

---

### Post by oldskool73 on 2006-09-19
possible, but sounds like a pain...

[http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html](http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html)
[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

---

### Post by dentaku65 on 2006-09-19
Yes it is possible to use vmware in Ubuntu and loading windows as virtual machine that resides in other partition on the same disk.

I used this guide and works well (it is not specific for Ubuntu, but you can adapt):
[http://yep.it/?5izxdd](http://yep.it/?5izxdd)


:cool:

---

### Post by BoyBlunder on 2006-09-19
I've already got a ntfs drive mounted, I'm just interested to see if I can get the full install working under vmware ;]

---

### Post by moore.bryan on 2006-09-19
*from what i've read, you need to install windows "into" vmware...*

---

### Post by dentaku65 on 2006-09-19
> **moore.bryan said:**
> *from what i've read, you need to install windows "into" vmware...*

non, no... I have
/dev/hda1 [xp]
/dev/hda2 [ubuntu]
I'm loading the virtualization of /dev/hda1 (xp) through vmware server running on Ubuntu (/dev/hda2)... see the link above.

---

### Post by moore.bryan on 2006-09-19
*really!?  are other people aware of this?  ;-)  everything i've read is people complaining about vmware needing a fresh install of windows.*

---

### Post by dentaku65 on 2006-09-19
It is wrote in the documentation... I'm using very well (well, I have to stop compiz when I'm loading vmware cos' lack of ram :-$ )

---

