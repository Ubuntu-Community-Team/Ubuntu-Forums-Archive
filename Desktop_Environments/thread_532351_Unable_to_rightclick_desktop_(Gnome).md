---
title: "Unable to rightclick desktop (Gnome)"
date: 2007-08-22
forum: Desktop Environments
---

### Post by [alterego] on 2007-08-22
For a day or two I have been unable to rightclick on my desktop (create folder etc.), the problem occurred out of nowhere.
I've tried to restart (ctrl+alt+backspace) and reboot the computer .. but nothing changes.
In Gnome failsafe I'm able to change desktopbackground and create folders/documents, remove folders etc. But when I reboot the computer the problem is back.

Any good ideas or suggestions to solve this problem?

Computer:
Intel Celeron 3 Ghz
768 Mb RAM
100 Gb. HDD

Ubuntu Feisty Fawn w. Gnome (allways updated)

---

### Post by Chymera on 2007-08-22
the x session usually breaks from time to time, i had my super key go on vacation until i found out how to reconfigure it. Stop the x session and run
```
sudo dpkg-reconfigure xserver-xorg
```
its pretty self-explanatory, but feel free to ask if you dont kpish any of the instructions.

---

