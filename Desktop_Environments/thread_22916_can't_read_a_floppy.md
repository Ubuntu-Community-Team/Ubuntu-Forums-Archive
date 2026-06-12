---
title: "can't read a floppy"
date: 2005-03-30
forum: Desktop Environments
---

### Post by lorap on 2005-03-30
does somebody know the solution to this question?
thanks.
pavel

---

### Post by dcraven on 2005-03-30
Do you mean you that the label sticker on the disk got smudged?

If not, you might want to be more specific in your requests for support.

~djc

---

### Post by lorap on 2005-03-30
i meant the system can't read the floppy,in other words it can't mount it.
that's the difficulty.

---

### Post by kafton on 2005-03-30
If you are talking about a single floppy that won't mount but other ones do, it's something wrong with that floppy.

If you are talking about floppies in general, type  "sudo modprobe floppy"  and see if that makes a difference. If this does allow you to mount the floppy, add  "floppy"  to your /etc/modules file.

Ed

---

### Post by rykel on 2005-04-07
Your system will not read the floppy drive, or the filesystem on the floppy drive?

What is the error message?

Try this, and see what error message(s) you receive...

mount /media/floppy0

If you received something about Ubuntu not being able to read the filesystem, simply update your fstab file like this:

sudo gedit /etc/fstab


Go to the line about fd0 and change "auto" to "vfat":

/dev/fd0        /media/floppy0  **vfat**    rw,user,noauto  0       0

Hope that helps!

---

### Post by lorap on 2005-04-08
hi friends!
yup,i've done already that,the same result.
but anyway,thank you all friends!
if i solve this difficulty i'll let you know.
thank you all again.
pavel

---

