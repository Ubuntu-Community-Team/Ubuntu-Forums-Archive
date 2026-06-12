---
title: "Upgrade ruined graphics"
date: 2010-07-07
forum: Desktop Environments
---

### Post by realmad on 2010-07-07
Hello,

The recent kernel upgrade to 2.6.32.23 from *.22 has spoiled my desktop graphics.  The taskbar at the bottom is stretched only half way to the monitor and I had a bouncing ball on the desktop which is dis-positioned and stuck , I cant remove it either.

What to do next?

Thanks in advance.

---

### Post by mörgæs on 2010-07-08
How does the machine behave, if you boot into the old kernel?

---

### Post by realmad on 2010-07-09
Its the same in old kernel as-well. Half screen task-bar and bouncing ball desktop widget stuck on screen.

---

### Post by mörgæs on 2010-07-09
If the problem came with an update, there is a chance that it is already discovered and a fix is in the making. 

I would wait a day or two and try 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

