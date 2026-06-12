---
title: "Terminal Tabs"
date: 2007-11-18
forum: Desktop Environments
---

### Post by tbrothers on 2007-11-18
UBUNTU 7.10 and Gnome 2.20

In gnome, when I start a terminal session the default is 1 tab.  I am always clicking File - Open Tab.

Is there any way that when starting a terminal session I can have 3 tabs as the default?

Thanks,
Terry

---

### Post by mouseboyx on 2007-11-18
You run it as (if you are using gnome):
```


gnome-terminal --tab --tab --tab

```So replace your launcher with that command.

If you ever wonder about things such as this type

nameofcommand --help

---

### Post by tbrothers on 2007-11-18
Thanks mouseboy

However, I forgot to mention that I open the terminal as root while logged in as terry.

This works
gksu gnome-terminal

This does not
gksu gnome-terminal --tab

Any suggestions?

---

### Post by mouseboyx on 2007-11-18
```
sudo su
gnome-terminal --tab --tab --tab

```

---

