---
title: "ALT-F2 and nautilus crash"
date: 2005-04-25
forum: Desktop Environments
---

### Post by bts on 2005-04-25
After the update from warty to hoary I have a problem with gnome: ALT-F2 should open a command line window but in fact the gnome-panel crashes. Additionally, if I right-click a file within nautilus and choose "open with another application", nautilus crashes. 

How can I debug this?

(On my laptop where I also performed the upgrade, these problems are not present)

---

### Post by tread on 2005-04-25
I really have no clue, but if this happened to me I would probably start by moving the nautilus config files in my home directory and then runnning nautilus so the defaults get loaded again.

Also, do you get any kind of error message? Start X from the console, by typing startx .. then switching to the console will show you errors. (You may have to disable gdm for this though)

---

### Post by pantulis on 2005-05-05
[QUOTE=bts]After the update from warty to hoary I have a problem with gnome: ALT-F2 should open a command line window but in fact the gnome-panel crashes. Additionally, if I right-click a file within nautilus and choose "open with another application", nautilus crashes. 

How can I debug this?

(On my laptop where I also performed the upgrade, these problems are not present)[/QUOTE]
 Same here, bts.  I attached a gdb to the running gnome-panel and found that the segmentation fault runs on 'strcmp' , so I guess it is some kind of weird bug related to the name of some application installed in your system.   (You see, the right click in nautilus does essentially the same: list the app names)

---

