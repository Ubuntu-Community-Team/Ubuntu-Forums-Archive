---
title: "Can't change screen resolution"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Betty Lynn on 2006-08-22
Hi,

Just installed ubuntu 6.6 and am trying to change the screen resolution to 800x600. I select 800x600 in the settings and click Apply but do not get the Keep this or not type dialog I expect. Instead, the screen goes weird (broken colors and black) then goes to a different screen asking for my userbame and password (incidentally, this also happened whilst trying the Live CD, I tried ubuntu as the username/pass but with no success). I enter them and then the desktop reloads but with the same resolution as before, 1024x768. I find it odd that I should have to provide my username/pass to do this, anyway, can anyone tell me what the problem might be?

Betty

---

### Post by croak77 on 2006-08-22
I'd suggest running from a terminal;

```
 sudo dpkg-reconfigure xserver-xorg
```

You can edit you screen resoultion. Then restart X.

---

### Post by Betty Lynn on 2006-08-23
Thanks, I have a task running on that machine at the moment so I'll try your suggestion later.

---

### Post by Betty Lynn on 2006-08-23
Well I tried that but didn't know the answer to some of the questions it asked, now everything is messed up and I can't access the desktop at all. Guess I'll have to reinststall and try again.

---

### Post by croak77 on 2006-08-24
You don't have to reinstall. Look in your /etc/X11 directory there is most likely the current xorg.conf as well as an old one or backup one. Just delete the bad xorg.conf and rename the old one.

---

### Post by Betty Lynn on 2006-08-24
Sorry, I should have said I have no GUI at all, not just the desktop. I tried to do what you said from the Live CD but didn't have the right permissions and the furthest I can get with the command line is that it will tell me /etc/X11/ is a directory. I think I should have posted in the Absolute Beginner Talk forum.

Thanks very much for your help anyway, I'm going to do a fresh install now as it will be the quicker option for me.

---

