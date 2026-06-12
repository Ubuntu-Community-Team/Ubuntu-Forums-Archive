---
title: "Second Gnome session in a window"
date: 2010-02-02
forum: Desktop Environments
---

### Post by daltore on 2010-02-02
So I remember from an installation of Ubuntu a couple of versions back that I managed to find a neat little program which allowed you to log into Gnome through a window while already in Gnome.  I can't for the life of me remember what it was called or find it again.  For those of you lost by my description, here's the setup:

In Gnome, as usual.  Go to the menu and open a program.  New Gnome login screen pops up inside a window.  Login to Gnome again in a different account without removing access to the first session.

Anybody know of a program that does this? It would be useful for me.

---

### Post by i.r.id10t on 2010-02-02
Xnest

Xnest :1 -query localhost

---

### Post by daltore on 2010-02-02
That's not what I was thinking of, but it looks like it'll work once I figure out why it's not working.

When I run that command, the window pops up but shows only black and my mouse disappears over top of it.  Anything else I should try?

---

### Post by Barriehie on 2010-02-03
While not -exactly- what you're looking for you can get another session frm CTRL-ALT-F1
login with your usual username
then at the prompt:
```

xinit /usr/bin/gnome-session -- :1

```

---

