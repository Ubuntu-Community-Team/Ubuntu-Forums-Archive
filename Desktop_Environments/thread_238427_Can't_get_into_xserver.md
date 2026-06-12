---
title: "Can't get into xserver"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Donnut on 2006-08-17
Hi all.  I changed a setting in ubuntu login screen preferences, now all I see in the login screen is "Network boot".  From here I can not get into my normal login screen.  I try to boot into recovery mode, login as steve(user) and get this error: 

xauth:  creating new authority file /home/steve/.serverauth.4019
X: user not authorized to run the X server, aborting.
xinit:  Server error.

What can I do?

---

### Post by b_martinez on 2006-08-17
Much of this answer depends on your experience with Ubuntu. If you can start the boot process, try to hit the 'e' key. this opens the grub editor. Highlight the line beginning "kernel ...." and hit the 'e' key again. type in the number '2' at the end of the line. This SHOULD boot you into a single user, text mode. Log in as root,[is this possible with Ubuntu?] and 'startx'. If Ubuntu acts like the others I've used, this will get you into your GUI and fix it from there. If you cannot log in as root, log in as your usual user and go from there.
hth
Bill

---

### Post by Donnut on 2006-08-17
In as root now, I just logged out and hit startx from recovery mode.  Not a very good idea, but all I could do at the moment.  If I hit startx from any usr mode, it gives me the self same error.

---

