---
title: "[SOLVED] switching display-managers causing annoyance"
date: 2007-11-18
forum: Desktop Environments
---

### Post by malachias on 2007-11-18
Hi

First of all, I noticed whenever I run compiz --replace, it says Xgl... Not Present (or something like that... compiz still works fine though) so I went ahead and installed xgl, but then it didn't detect my nvidia anymore, so I just uninstalled the packages I installed and set everything back the way it was.
Problem: Now, every time I log in, a box pops up that says that X expected my keyboard to be pc101, but gnome has it saved as pc105, which settings do I want to use? How can I tell it to remember my selection?

Second, I installed KDE, then removed it again (since using both DE's cluttered up my menus too much). In order to figure out exactly which packages I had to get rid of I went to /var/lib/dpkg/info and ran "ls -l|grep 2007-11-18 15:2", and then apt-get remove purge'd them. I went ahead and fixed the default display manager back to /usr/sbin/gnome, and everything's fine and dandy, except that now, gnome runs on Ctrl-Alt-F9 instead of Ctrl-Alt-F7. This is just a small annoyance, but I'd like to know how to get it back to the way it was.

Thanks!!

Malachias

---

### Post by malachias on 2007-11-21
Oddly enough, now (several days later) the second problem seems to have fixed itself on its own... odd.

---

### Post by malachias on 2007-12-13
the problem somehow fixed itself on its own over the next week or so. I have no idea how or why. Sorry to not be more helpful to anyone else experiencing the same issues.

---

