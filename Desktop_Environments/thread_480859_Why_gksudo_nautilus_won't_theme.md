---
title: "Why gksudo nautilus won't theme?"
date: 2007-06-21
forum: Desktop Environments
---

### Post by orb9220 on 2007-06-21
See the pics is there a reason that a gksudo nautilus will not theme to system settings?

Is there a way around it?

Thanks any help is always appreciated.

---

### Post by yabbadabbadont on 2007-06-21
```
sudo -i
ln -s /home/yourusername/.themes
ln -s /home/yourusername/.icons
ln -s /home/yourusername/.fonts
ln -s /home/yourusername/.gtkrc-1.2

```
Hopefully, that should do it.

---

### Post by ThrobbingBrain66 on 2007-06-21
To get the root account to use your themes, etc., issue the following commands:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by orb9220 on 2007-06-21
Sorry thanks for the info but that didn't work for either.

Tried:

> sudo -i
ln -s /home/orb/.themes
ln -s /home/orb/.icons
ln -s /home/orb/.fonts
ln -s /home/orb/.gtkrc-1.2


no go then tried:

> sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons

still getting the ugly nautilus instead of the Puriteey  Nautilus.

---

### Post by orb9220 on 2007-06-21
Never mind it seems the Murrina-GrigioProfondo theme I got does not totally work. I can change to others and it works fine.

Isn't there any theme standards at gnome-look? I remember from last year I ran into this issue and just changed themes.

But thanks for your quick response.

The theme works for everything but a gksudo nautilus don't know why it would work for everything else and not that.  If you know why please share.

---

### Post by Candle Jack on 2008-07-14
Came across this post in google.. don't know if you're not supposed to bump but since it has such a high pagerank I might as well finish it out.

When you gksudo nautilus, you're running it as the root user. You've configured your theme for your user, but not root. Try doing:

```
sudo gtk-theme-switch2
```

This will let you pick a theme for the root user. Personally I have it set to a red version of the theme I use so that it's always as obvious as possible that I'm running as root.. just keeps me careful :KS

---

### Post by YaroMan86 on 2008-07-14
Gotta make sure its installed first.

---

