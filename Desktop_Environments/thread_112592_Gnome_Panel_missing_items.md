---
title: "Gnome Panel missing items"
date: 2006-01-04
forum: Desktop Environments
---

### Post by fakie_flip on 2006-01-04
I did a fresh install of Ubuntu 5.10 and started downloading and installing my favorite software through Synaptic. After messing with my computer for about a day and installing Xfce4, my gnome menu was screwed up. I have reinstalled Ubuntu 5.10 and choose not to get Xfce4. My gnome panel has screwed up again but this time not as bad. "Image Viewer" is missing from Applications/Graphics again. I only have three items there, and I was supposed to have four. Is there a way to set gnome back to default or fix this? I still have Image Viewer installed, and I like it better because I can switch to another picture quickly without reopening the app. Tell me if your gnome panel still has "Image Viewer". I found out "Image Viewer" in the gnome menu is called Eye of Gnome or eog.

---

### Post by Omnios on 2006-01-04
try using " update-menus " in terminal
```
update-menus
```

---

### Post by fakie_flip on 2006-01-04
[QUOTE=Omnios]try using " update-menus " in terminal
```
update-menus
```[/QUOTE]

chris@ubuntu:~$ update-menus
bash: update-menus: command not found
chris@ubuntu:~$

---

### Post by fakie_flip on 2006-01-04
Will "dpkg-reconfigure gnomepackagename" fix it? What gnome package is the correct one to reconfigure?

---

### Post by Omnios on 2006-01-04
I thin that works with the "menu" program found in synatic not shure but it just worked on my computer. Another trick was to kill menu and have it reload

---

### Post by fakie_flip on 2006-01-04
I figured out how to fix the problem. It was not very hard. Anyone who has this problem should do the same thing I did. In the gnome menu goto --> Applications/System Tools/Applications Menu Editor and check off the box in there. Going to Add Application will not correct the problem.

---

