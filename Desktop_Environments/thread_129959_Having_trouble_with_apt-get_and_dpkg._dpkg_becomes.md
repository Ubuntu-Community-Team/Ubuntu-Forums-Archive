---
title: "Having trouble with apt-get and dpkg. dpkg becomes unresponsive."
date: 2006-02-15
forum: Desktop Environments
---

### Post by Trickyphillips on 2006-02-15
Greetings,

I ran into a trouble while trying to apt-get dist upgrade a few days ago. When it was gstreamer0.8-gtk's turn to be installed, dpkg became unresponsive and I was forced to kill it manually. Since then, I've been getting this:

```
ron@trickyphillips:~$ sudo apt-get install audacity
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
ron@trickyphillips:~$ sudo dpkg --configure -a
Setting up gstreamer0.8-gtk (0.8.11-0ubuntu5) ...
```

At this point dpkg becomes unresponsive as previously stated, and the only way to terminate it is with kill/killall.

Any suggestions as to what I should do?

Thanks,
Ron

---

### Post by Jason_25 on 2006-02-15
sorry

---

### Post by anirban.sam on 2006-02-15
try,
sudo apt-get remove gstreamer0.8-gtk, then

sudo apt-get update

---

### Post by Trickyphillips on 2006-02-15
Thanks for the reply. Unfortunately, apt-get doesn't want to remove anything right now.

Same error:
> ron@trickyphillips:~/Desktop$ sudo apt-get remove gstreamer0.8-gtk
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


---

### Post by Trickyphillips on 2006-02-15
While I hate to bump topics, I'd like to bring this topic back to the front page. Any further suggestions would be appreciated. Thanks. :)

---

### Post by Trickyphillips on 2006-02-15
Well... as a Unix user I'm ashamed to admit it, but I've rebooted my laptop and killed my uptime (Even with my Windows computers, reboots are uncommon). 

Things are working fine now, fortunately. Sorry to waste your time.

---

