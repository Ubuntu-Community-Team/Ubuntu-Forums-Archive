---
title: "Copying File from Desktop to Floppy"
date: 2005-10-30
forum: Desktop Environments
---

### Post by jrc on 2005-10-30
Can someone give me or point me to instructions for copying a file from the Desktop to a floppy disk?  I've searched and searched for instuctions to no avail.  Thanks.

---

### Post by OBnascar on 2005-10-30
[QUOTE=jrc]Can someone give me or point me to instructions for copying a file from the Desktop to a floppy disk?  I've searched and searched for instuctions to no avail.  Thanks.[/QUOTE]

I'll be waiting for an answer to this myself, as I have never been able to copy to a floppy either.

---

### Post by NewbieNik on 2005-10-30
[QUOTE=OBnascar]I'll be waiting for an answer to this myself, as I have never been able to copy to a floppy either.[/QUOTE]


What have you tried and what was the outcome? The reason I ask is that I have done this on Breezy by dragging and dropping using Nautilus without any issues.
Have you had error messages? Have you formatted the floppy? Is the floppy drive showing in Places>Computer?

---

### Post by jrc on 2005-10-30
Perhaps my question is too elementary for this forum, but I couldn't figure out where else to post it since the guidelines for the Absolute Beginner forum say I shouldn't post there if I've ever used the Command line.

Anyway, I found the answer myself.  You can find it at this URL:

[http://www.linux.org/lessons/beginner/l13/lesson13d.html](http://www.linux.org/lessons/beginner/l13/lesson13d.html)

I deviated slightly from the instructions given, however.  I did not create a "floppy" directory at root.  Instead, I noticed there is already a "floppy0" directory in the "media" directory (at least there is with Breezy Badger), so I just used that.  So, I used the following syntax:

mount -t ext2 /dev/fd0 /media/floppy0

I then copied the file from my Desktop to /media/floppy0.

It worked after I tried a few times.  I think I got my syntax wrong on the first few attempts.  I also ended up with an extra directory on the floppy called "lost+found," but it doesn't seem to make any difference.  The file I wanted to copy appeared on the floppy also.

Oh, don't forget to unmount after you finish copying your file.  The command in my case was:

umount /media/floppy0

Notice there's no "n" after the "u" in "umount."

Good luck.

---

### Post by OBnascar on 2005-10-30
[QUOTE=NewbieNik]What have you tried and what was the outcome? The reason I ask is that I have done this on Breezy by dragging and dropping using Nautilus without any issues.
Have you had error messages? Have you formatted the floppy? Is the floppy drive showing in Places>Computer?[/QUOTE]

When I try to drag & drop, It is another one of those "permission" issues. I have permission on the text file that I want to copy to the floppy, but not on the floppy drive its self. This permission thing in ubuntu has got me stumped. I have tried documentations on getting permission but none of them has worked for me.

I would be very, very happy on finding out why I can not get permission !

Using 5.10

---

