---
title: "Problem"
date: 2009-04-05
forum: General Help
---

### Post by F6F Freak on 2009-04-05
I dual boot Vista-Ubuntu. 
I held the power button down because I needed (i repeat needed)a rapid shutdown. Ubuntu took it as a crash and will boot up, give me my log in screen, but once I log in it gives me a bunch of error messages on top of... BLACK! There is nothing but cursor, errors, and black! HELP!

---

### Post by krishna1650 on 2009-04-05
> **F6F Freak said:**
> I dual boot Vista-Ubuntu. 
I held the power button down because I needed (i repeat needed)a rapid shutdown. Ubuntu took it as a crash and will boot up, give me my log in screen, but once I log in it gives me a bunch of error messages on top of... BLACK! There is nothing but cursor, errors, and black! HELP!

what are the errors?
you can try to log in by text mode using alt+clt+f1, check if you can log in properly or there is also error.

---

### Post by F6F Freak on 2009-04-05
...Something with evolution alarm notifier, gnome power manager, and NFS locks.

---

### Post by yamarc on 2009-04-05
Can you post the exact error messages you are getting?

---

### Post by krishna1650 on 2009-04-05
> **F6F Freak said:**
> ...Something with evolution alarm notifier, gnome power manager, and NFS locks.

did you try to log in by text mode?

---

### Post by F6F Freak on 2009-04-05
No on both counts.
1. I cannot open anything, so no screenshot, and no copy-paste.
2. Haven't had the time.
I will, when I have time, record the messages on paper and post them.
I recall it said that one of the problems was "NFS locks imposed due to system crash" That seems to be the root problem...

---

### Post by F6F Freak on 2009-04-05
Yes, I can log in text-style.
There are multiple errors, all with one thing in common:
GNOME power manager failed to install, and "stale NFS locks due to system crash"
That seems to be the root cause.
EDIT: The GNOME power manager had it's own bubble.

---

### Post by oldos2er on 2009-04-05
Try booting into recovery mode to run fsck.

---

### Post by jpeddicord on 2009-04-05
> **F6F Freak said:**
> Yes, I can log in text-style.
There are multiple errors, all with one thing in common:
GNOME power manager failed to install, and "stale NFS locks due to system crash"
That seems to be the root cause.
EDIT: The GNOME power manager had it's own bubble.

Interesting.. are you using any networked filesystems, such as folders shared from other computers? NFS stands for Networked Filesystem -- you shouldn't be seeing that error if you're not using one.

---

### Post by F6F Freak on 2009-04-06
No, I do dual-boot. That may have something to do with it. However, I read a thread where a guy had the same problem on an eee-pc, far to small to dual-boot.

---

### Post by F6F Freak on 2009-04-06
I tryed running fsck, no help. Going to reinstall...
Jaunty beta?
Xbuntu, Kbuntu, or Ubuntu?

---

### Post by infallible on 2009-04-07
I came across your thread while searching for the solution to a similar problem, and thought I would share what I've learned (or at least my theory.) 

The system crashed, and gconf didn't close out properly. It has a function that locks critical files, etc for the use of the individual user. The crash caused them to remain locked, and therefore inaccessible.  ctrl-alt-1 brings up a terminal, ctrl-alt-7 brings up  a gnome (windowed) session. To remedy this, try typing ```
 mv ~/.gconfd/saved_state saved_state.old

``` into your terminal and reboot, or perhaps its only necessary to ctrl-alt-backspace and log in again.   It was either this that fixed it, or "dpkg-reconfigure gconf<tab><tab>" and reconfiguring everything that started with gconf. either way, these steps allowed me to log in again.

best of luck,
Pete

---

