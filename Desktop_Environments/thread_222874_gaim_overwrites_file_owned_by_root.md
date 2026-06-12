---
title: "gaim overwrites file owned by root"
date: 2006-07-25
forum: Desktop Environments
---

### Post by ishtvan222 on 2006-07-25
In gaim all the away messages are stored in status.xml and are not account specific, so one account could make an away message and it would show up in someone elses account because they share the same status.xml.

I got tired of other having other peoples away message always show up as mine in gaim. So I decided to lock the status.xml so that no one could make new away messages. I took away write permissions and was unable to write to the file using gedit, but gaim was still able to write to the file. 

Then I decided to let root be the file owner (with only root with write permission) so that gaim could only write to status.xml when running as root. But gaim was still able to change the file owner back to the default user when I used gaim to write to status.xml

Is this a bug or am I missing something?

---

### Post by exif on 2006-07-25
The only explanation I can think of is if you're running gaim with sudo.

---

### Post by ishtvan222 on 2006-07-26
I start gaim from menu in GNOME, and when I do a ps aux it shows that gaim is running under my normal username.

---

