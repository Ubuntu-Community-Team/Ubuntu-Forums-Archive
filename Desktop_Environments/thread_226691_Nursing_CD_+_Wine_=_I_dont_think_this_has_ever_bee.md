---
title: "Nursing CD + Wine = I dont think this has ever been asked?"
date: 2006-07-31
forum: Desktop Environments
---

### Post by iaregerard on 2006-07-31
Hello all, I'm a nursing student and have been a big fan of ubuntu for the past couple of months now. As I've been studying on my XP machine, I've wanted to use my Saunders NCLEX CD on Ubuntu. I got it installed on wine, but the program itself has to read from the CD, which unfortunately doesn't work. I was just wondering how I can get it to read off the CD, or if I could use a program like Alcohol 120 to read it as a virtual drive. Any help would be appreciated. Thanks.

---

### Post by Paerez on 2006-07-31
EDIT: What I previously posted was incorrect, here is what I was looking for:

> This goes in .wine/dosdevices. Here:
lrwxrwxrwx 1 ray ray 10 Apr 24 11:44 c: -> ../drive_c
lrwxrwxrwx 1 ray ray 10 Apr 24 11:44 d: -> /media/cdrom
lrwxrwxrwx 1 ray ray 8 Apr 24 11:44 d:: -> /dev/hdc
lrwxrwxrwx 1 ray ray 1 Apr 24 11:44 z: -> /
from:[http://www.linuxquestions.org/questions/showthread.php?p=2246242#post2246242](http://www.linuxquestions.org/questions/showthread.php?p=2246242#post2246242)

To make a cdrom link like D: and D:: in the above, you type:
```
ln -sf /media/cdrom d\:
ln -sf /dev/hdc d\:\:
```

---

### Post by keyshawn on 2006-07-31
There's an 'add a CD or hard drive' section on the wine entry on the ubutnu wiki. 

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Let us know if the directions worked for you or not. :D

regards,
keyshawn

---

### Post by Paerez on 2006-07-31
oh yeah that's way easier than my way!

I wish I was more familiar with the solutions on help.ubuntu.com, saves a lot of typing.

---

### Post by iaregerard on 2006-08-01
Hey guys, good news. It works!!! Although it runs a little sluggish, but I don't think that can be helped. I didn't find anything on the wiki in terms of making it run more efficiently. But it's all good, I'm really glad it works now. Thank you again!

---

