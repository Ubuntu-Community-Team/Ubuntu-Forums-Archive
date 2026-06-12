---
title: "sudo aptitude"
date: 2012-06-19
forum: Desktop Environments
---

### Post by KegHead on 2012-06-19
Hi!

I've finally made the migration to Xubuntu (12.04)!

One problem: sudo aptitude install linux-image -f
does not seem to work.

Anyone?

KegHead

---

### Post by rukiaEnix on 2012-06-19
Could you please post the error message?

---

### Post by KegHead on 2012-06-20
jim@jim-desktop:~$ sudo aptitude install linux-image -f
sudo: aptitude: command not found

---

### Post by drs305 on 2012-06-20
KegHead,

Aptitude is no longer installed by default on the recent releases of the Ubuntu family. 

You have to install it:```

sudo apt-get install aptitude
```

---

### Post by cottfcfan on 2012-06-20
Have you installed aptitude?
If not the command is apt-get.

drs305... you beat me to it.

---

### Post by KegHead on 2012-06-20
Hi!

It worked like a charm!

(I should have known this!)

Thanks!

KegHead

---

