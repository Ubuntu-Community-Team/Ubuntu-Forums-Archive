---
title: "Running dual boot and time keeps changing!"
date: 2005-10-27
forum: Desktop Environments
---

### Post by i30i3i3y on 2005-10-27
Funny problem this, I'm sure its something stupidly simple.

I'm running Breezy and XP in dual boot. Everythings fine in breezy, but when I switch back to XP the time goes back an hour. If I continually use XP- all ok, as soon as i use XP after a session in breezy the time in xp goes back by an hour. Must be something to do with Daylight Savings or something. Any ideas?

---

### Post by Gordonbp531 on 2005-10-27
I found this. It's something to do with the way XP keeps time when daylight saving is checked. I can't remember the details, but it seems its XP at fault not Ubuntu.

---

### Post by bernardfrancois on 2006-03-26
You can easily fix that... just make sure your time zone is set the same in windows as in ubuntu.

Then just adjust your clock so it matches your local time

I posted this before in another thread, just search on threads where I posted that were about this issue. I think you have to set your windows time zone to GMT, but I don't know for sure any more.

---

### Post by ronmarley1 on 2006-03-26
I had the same problem and this thread fixed it.  See the second post (first reply).
[http://www.ubuntuforums.org/showthread.php?t=145321&highlight=time+zone+gmt](http://www.ubuntuforums.org/showthread.php?t=145321&highlight=time+zone+gmt)

---

### Post by Irony on 2006-03-26
[PHP]sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS[/PHP]

Change;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes[/PHP]

to;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no[/PHP]

Probably during your install you chose UTC but the above changes it back to local time.

---

### Post by alime on 2006-05-04
Thank You!

---

