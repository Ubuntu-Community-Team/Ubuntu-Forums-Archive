---
title: "My desktop icons keep disappearing."
date: 2009-03-28
forum: Desktop Environments
---

### Post by chris_andrew on 2009-03-28
Hi,

I've just done a new install of Xubuntu.  Everything is fine except my desktop icons keep disappearing.

It seems that I can get them back by going to

```
Settings > Settings Manager > Desktop
```

and selecting 

```
Allow xfce to manage the desktop
```

For some reason though, this change isn't persistent, and moments later my icons disappear again.

Has anyone else had this problem?

Cheers,

Chris.

---

### Post by wannjanjic on 2009-03-28
It looks like you're having problem with xfdesktop. Try running it from terminal and watch for the output when icons disappear.

---

### Post by DaanVB on 2009-04-09
I have a similar problem. Every time I boot up and when I change the widget theme to a GTK theme, the desktop is managed by gnome instead of xfce. I need to do the above to get the xfce desktop back everytime. There seem to be a lot of people who have problems with their desktop "disappearing" on xfce. Maybe it's all the same problem? I have no idea how to permanently fix it though.

---

### Post by chessnerd on 2009-04-09
I had a similar problem when I first tried to use the Nautilus file manager under Xubuntu. When I input the command it changed the desktop to Gnome. I had to run the command as Nautilus --no-desktop and then it didn't change to Gnome anymore. I don't know if you might be able to change your command using the same or a similar parameter, but you could try it.

---

