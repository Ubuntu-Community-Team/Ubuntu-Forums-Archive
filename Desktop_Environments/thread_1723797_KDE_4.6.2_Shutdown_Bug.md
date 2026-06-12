---
title: "KDE 4.6.2 Shutdown Bug"
date: 2011-04-07
forum: Desktop Environments
---

### Post by EmyrB on 2011-04-07
Hi All,

There is a bug in KDE SC 4.6.2 that affects shutdown. When you try to shutdown , you get to a tty session instead. See this link [https://bbs.archlinux.org/viewtopic.php?pid=914637]("https://bbs.archlinux.org/viewtopic.php?pid=914637").

Now if I read it right, the shutdown command has a wrong switch, namely -p, How do I solve this in Kubuntu as there is no kdmrc to edit?

Cheers

EmyrB

---

### Post by Odur on 2011-04-07
There is: /etc/kde4/kdm/kdmrc

Use the switch -P (upper case, not lower) or -h

---

### Post by EmyrB on 2011-04-08
Cheers Odur, that did the trick.

---

