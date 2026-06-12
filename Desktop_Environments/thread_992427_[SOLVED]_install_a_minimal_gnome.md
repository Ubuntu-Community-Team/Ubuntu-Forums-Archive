---
title: "[SOLVED] install a minimal gnome"
date: 2008-11-24
forum: Desktop Environments
---

### Post by Darth_tater on 2008-11-24
I am installing 8.10 server edition on my home file server.  This server will have many functions, some of which require a GUI.  I would like to use Gnome, but since this is a file server, It is my benefit to have as much free space as possible...
So my question is this:
How can in install *just* gnome and the file browser nautilus...?  I don’t need open office, the games, widgets, and all the other crap that comes with the normal Gnome install.  How can I best slim down ubuntu’s default gnome install?  Is it better for me to use the default installer then cut things out, or should I use the server install then can I specify just the minimal packages that I need to install?

Thanks for any and all help you can give me!

---

### Post by kerry_s on 2008-11-24
```
sudo apt-get install xorg gnome-core
```

are you sure you really need gnome? using a light wm will save you more resources and space.

---

### Post by Darth_tater on 2008-11-24
I have thought about it, and yeah other light weight window managers came up.  I guess I’m just going to stick with what I know... especially since this computer will occasionally have to function like a full fledged desktop.

Thanks for your help!

---

