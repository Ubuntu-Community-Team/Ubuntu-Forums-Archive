---
title: "gnome  boots on top of KDE"
date: 2008-12-27
forum: Desktop Environments
---

### Post by Docaltmed on 2008-12-27
I'm using an HP TX2510 running kernel 2.6.27-11, originally using Gnome desktop.

I added KDE according to instructions, and now when I choose KDE at startup, the KDE desktop will load...and then Gnome loads, and I end up with the Gnome panels on top of the KDE panel. Everything else looks KDE.

What's going on? How do I stop this?

---

### Post by Captain_tux on 2008-12-28
Can you post a screenshot?

---

### Post by Docaltmed on 2008-12-29
Here you go:

---

### Post by Docaltmed on 2008-12-29
One other thing. When I log off or shut down, the KDE desktop closes, which reveals my gnome desktop, before logging off. It really does appear that the computer is loading gnome then loading kde on top of that.

I have tried uninstalling the gnome desktop but that didn't change anything. So I reinstalled gnome, and that didn't change anything either.

---

### Post by the yawner on 2008-12-29
Uhm.. Kindly check if nautilus is running on your KDE session?

---

### Post by Docaltmed on 2008-12-29
Hi,

Nautilus is running, as is gnome-panel (there appear to be 2 instances of gnome panel running, both with the same description as "top expanded edge panel". 

Just for laughs, I tried killing these processes through the system monitor. They refused to die.

EDIT: I also tried "killall nautilus" in the terminal and then restarting the x-server (ctrl-alt-backspace). Nautilus and the two gnome panels are still there.

---

### Post by Docaltmed on 2008-12-29
I gave up. There were just too many things going wrong. I did a clean reinstallation of Kubuntu. Now I have other problems, but at least the desktop works.

---

