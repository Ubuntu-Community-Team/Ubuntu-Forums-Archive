---
title: "What's the difference between the filesystems?"
date: 2006-01-17
forum: General Help
---

### Post by hk_2999 on 2006-01-17
How can I compare ReiserFS, ext2, ext3 and various other filesystems out there.

I want to know which is best for my system.

Thanks in advance.

---

### Post by stuporglue on 2006-01-17
Running a desktop machine? Ext3 is a safe, sane, choice. 

Ext3 is essentially a journaled version of Ext2, which makes it less likely to lose your data in a crash. 

ReiserFS has some cool features supposedly, such as fitting in small files better (IIRC), but I don't think it makes a huge difference to most users.

---

### Post by ape on 2006-01-17
Try this link for more info:

[http://www.novell.com/documentation/suse91/suselinux-adminguide/html/apas02.html]("http://www.novell.com/documentation/suse91/suselinux-adminguide/html/apas02.html")

---

