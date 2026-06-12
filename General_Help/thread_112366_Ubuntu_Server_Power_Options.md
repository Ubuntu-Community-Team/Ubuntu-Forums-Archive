---
title: "Ubuntu Server: Power Options"
date: 2006-01-04
forum: General Help
---

### Post by Mortuis on 2006-01-04
I tried [asking this question]("http://www.ubuntuforums.org/showthread.php?t=111761") in Absolute Beginner talk, since I'm a beginner, but it's been over 24 hours without a responce, so I'm thinking maybe it's not a beginner issue.

This is one of those "How do I do that thing I did in windows" questions. In windows I can get to a "Power Options" menu where I tell the hard disk to stop spinning after X minutes of inactivity, same with the monitor.

I have Ubuntu (5.10) Server installed on a Thinkpad 770, and I do everything on it via SSH, so the monitor is never on, so I'm not really worried about that. But the hard disk is always spinning happily, and I'd like to put a stop to that.

How does one tell the hard drive to stop spinning after it's hasn't been used for 15 minutes or whatever?

---

### Post by hw-tph on 2006-01-04
Try reading hdparm(8). The -S option to hdparm will set the spindown time but they use sort of a tricky timing scheme so make sure to read the manpage. After verifying it works by using hdparm from the shell, edit /etc/hdparm.conf to set whatever options you like.


Håkan

---

### Post by Mortuis on 2006-01-04
[QUOTE=hw-tph]Try reading hdparm(8). The -S option to hdparm will set the spindown time but they use sort of a tricky timing scheme so make sure to read the manpage. After verifying it works by using hdparm from the shell, edit /etc/hdparm.conf to set whatever options you like.


Håkan[/QUOTE]
Thanks for the reply.  I'll play around with that later tonight.

---

