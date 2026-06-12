---
title: "I forgot my root Password."
date: 2006-07-14
forum: Desktop Environments
---

### Post by Zingomoos135 on 2006-07-14
i realize that i made a HUGE mistake by not writing the password down, but i can't log in as root anymore. ](*,) 

does anyone have a suggestion for helping me get it back??

---

### Post by scxtt on 2006-07-14
boot into recovery mode, you'll be root - type **passwd** and enter a password you can remember ...

---

### Post by ciscosurfer on 2006-07-14
1) Boot to recovery mode where you are automatically root; change your root password there.  

OR (if for some reason you can't get to your recovery partition)

2) Boot from a live-distro, mount your drive, add/change a new user; add/change your root password.  :D

---

### Post by Azyx on 2006-07-15
I tried this and give a password in recovery mode, but when a boot into the gnome, autologgin as a user, so didn´t the sudo + new password work, but i can log in as root with su + new password. It seems like the sudo password havn´t changed?

---

### Post by Azyx on 2006-07-15
Ah. I just find out. After passwd I type the user, in the root promt :)

---

### Post by Maheriano on 2006-07-15
I never did specify a password for root and so I'm having trouble doing > su - root

How do I boot into recovery mode to change it?

---

### Post by Maheriano on 2006-07-15
Nevermind, I got it.

> sudo passwd root

---

