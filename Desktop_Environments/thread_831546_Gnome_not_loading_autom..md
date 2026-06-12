---
title: "Gnome not loading autom."
date: 2008-06-16
forum: Desktop Environments
---

### Post by ben44b on 2008-06-16
I wanted to try KDE for a while for a test drive. Decided that I preferred GNOME. Removed all of KDE but now when I turn on the computer, I have to login and type sudo gdm to get to the GNOME gui. I tried tinkering with the Login Manager but without success.

Thanx.

---

### Post by sdennie on 2008-06-17
You could try doing the following in a terminal:

```

sudo dpkg-reconfigure gdm

```

That should allow you to choose which display manager you want to use.

---

