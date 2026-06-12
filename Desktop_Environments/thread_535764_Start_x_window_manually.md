---
title: "Start x window manually"
date: 2007-08-26
forum: Desktop Environments
---

### Post by jimhce on 2007-08-26
Hi,

I don't want to start X window automatically, how can I change rc.d setting to let me to start X window manually from a text console?

Thank you.

Jim

---

### Post by aysiu on 2007-08-27
Try ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm stop
sudo apt-get remove kdm
sudo apt-get remove gdm
```

---

### Post by zoobave on 2007-08-27
There is  no need to remove KDM or GDM.
Just remove the entry in the following file
/etc/X11/default-display-manager  

If you want to start the X server, just give the command

# gdm

regards,
zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---

### Post by jimhce on 2007-08-27
Thank you all. I guess I can also manually either to run gdm or kgm. Very good indeed.

Thank you.

Jim

---

