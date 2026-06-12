---
title: "How to set custom keystrokes?"
date: 2011-09-06
forum: Desktop Environments
---

### Post by jfed on 2011-09-06
Hello. I have just recently switched from GNOME2 to Xfce, and I am finding that many short cut keystrokes I used to use in Gnome aren't working on Xfce. I'm not sure if this is some sort of bug/issue, or they just don't work on Xfce by default. In either case, I'd like to know how to fix these/set these to work:

Ctrl+Alt+Backspace to restart the GUI
and
Ctrl+Alt+T to bring up a terminal

How can I set those to work in Xfce4? I'm using Ubuntu 10.10

Thanks in advance! ):P

---

### Post by azertyh on 2011-09-06
hello,
look at settings > settings manager > keyboard > application shortcuts.

---

### Post by raja.genupula on 2011-09-06
[http://lifehacker.com/256955/configure-custom-keyboard-shortcuts-on-ubuntu](http://lifehacker.com/256955/configure-custom-keyboard-shortcuts-on-ubuntu)


it is used  to set your own shortcuts keys

---

### Post by jfed on 2011-09-06
> **azertyh said:**
> hello,
look at settings > settings manager > keyboard > application shortcuts.

Thanks! Worked great to fix the terminal shortcut, but what is the command to restart the Xfce desktop, if you know?

---

### Post by kerry_s on 2011-09-06
> **jfed said:**
> Thanks! Worked great to fix the terminal shortcut, but what is the command to restart the Xfce desktop, if you know?

xfwm4  --replace

edit: the xfce desktop is several apps combined, that command is for the window manager.

---

