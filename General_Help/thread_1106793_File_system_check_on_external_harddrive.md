---
title: "File system check on external harddrive"
date: 2009-03-26
forum: General Help
---

### Post by _sAm_ on 2009-03-26
Hi

Quick question;
If you have an external hard drive(USB, ext3), should I run fsck manually on it from time to time since the system will not do it(like on the internal hard drives)?

I have never thought of it before now – can you get problems if you never do it? The disk have been mounted and used a lot without any check:-/

---

### Post by mcduck on 2009-03-26
Yes, manually checking the drive every now and them would be a smart idea.

Every hard disk will fail, sooner or later, and checking the drive with fsck will at least give you a change to notice that the drive is producing errors before it stops working.

How often you should check it depends of course on how much you use the drive and how important data you have on it.

---

### Post by _sAm_ on 2009-03-26
Ok, thanks!

I did run a check now and no errors. Its my backup, so I guess I will run the check from time to time. 


They should find a more easy solution for this, not very friendly for new users(!).

---

### Post by mcduck on 2009-03-26
Might be a bit hard, for example autochecking removable drives when plugged in would be at least a bit annoying.. People usually expect the drive to be accessible instantly when plugged in instead of sometimes having to wait, possibly for a long time if the drive is big one.

Of course you can just forget about checking removable drives, for example I don't think I've ever heard of a Windows user running chkdisk on removable FAT drives (at least if the drive hasn't already failed to work). And Ext definitely is more stable FS than FAT is, so you are safer as it is without doing any extra checking.

So I would consider the fsck on removable drives more as a extra measure that you can do if you put high value on your data. It's smart thing to do, but not something that you should be too worried about.

---

