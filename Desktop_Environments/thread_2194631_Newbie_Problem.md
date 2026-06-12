---
title: "Newbie Problem"
date: 2013-12-19
forum: Desktop Environments
---

### Post by limestorm on 2013-12-19
I am not a newbie, but I have made a newbie mistake. I had two display managers installed on my system at once, and I only wanted one. I decided to uninstall the one I did not want. I forgot to switch the other to default though, and I uninstalled SLiM without switching GDM to default. My OS will not start up now. How do I fix this without losing all my system files?

---

### Post by deadflowr on 2013-12-19
From the tty1 console (press ctrl+alt+F1-6) login and then try
```
startx
```

if that works, open a terminal and reconfigure the display manager
try
```
sudo dpkg-reconfigure gdm
```
then choose gdm.
Then restart the system.

---

### Post by limestorm on 2013-12-19
Thanks a lot! I felt stupid for having to ask this... It worked though! This forum has better support than any large company's support system.

---

