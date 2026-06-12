---
title: "Setting non-listed &quot;open with&quot; programs"
date: 2011-12-28
forum: Desktop Environments
---

### Post by mkhc on 2011-12-28
I'm trying to get used to Unity - having given up once and slowly tried Gnome 3, Kubuntu and Xubuntu I'm back again to what I'm currently finding the best of a bad bunch. I'm beginning to find answers to most of my problems. This is one I can't seem to find an answer for;

When setting an "open with" for a particular type of file (in this case audacity) I can't find audacity in the list of programs available.

I used to be able to set a specific program path at the bottom of the "Open With" dialogue in Gnome2.x but the only option now is search on the internet. Is there any way to add programs to this list or set my own path?

Many thanks in advance

Mark

---

### Post by mkhc on 2011-12-28
I tried Gnome 3 and discovered that this isn't a unity problem.

By following this guide ( [https://bbs.archlinux.org/viewtopic.php?id=118966](https://bbs.archlinux.org/viewtopic.php?id=118966) ) I found that all that was wrong was a missing "%U" in my /usr/share/applications/audacity.desktop file.

As soon as I added the " %U" at the end of the line "Exec=audacity"  Audacity was available in the open with list.

---

