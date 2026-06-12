---
title: "True transparency in xfce4-terminal, XChat"
date: 2007-03-02
forum: Desktop Environments
---

### Post by abstrustication on 2007-03-02
Important info: Xubuntu, Edgy Eft, Xfce 4.3.99.1

Hey all, I've got the compositor working and I love that my inactive windows are "dimmed."

However, I've been trying to make xfce4-terminal have truely transparent backgrounds for a while now and it's just not working.  It seems to be stuck in using the desktop background.  I'm having the same problem with XChat.

Anyone know why this might be?

---

### Post by raul_ on 2007-03-13
Been looking for this one for quite a while now...i found some patches but i can't get them to work.

---

### Post by mcduck on 2007-03-13
As the GTK toolkit that most Gnome/XFCE apps use doesn't have support for true transparency, the feature has to be specifically implemented in the program itself. I know that Gnome-terminal supports it, but XChat doesn't. I haven't tried xfce4-terminal in long time but most likely it just doesn't have support for true transparency either.

---

### Post by raul_ on 2007-03-13
Yeah, but it kinda sucks to load the gnome libraries because of a terminal :) i'll just use the xterm look. It's pretty sleek :cool:

---

