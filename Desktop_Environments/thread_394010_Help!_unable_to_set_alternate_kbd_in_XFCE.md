---
title: "Help! unable to set alternate kbd in XFCE"
date: 2007-03-26
forum: Desktop Environments
---

### Post by ac7ss on 2007-03-26
I am running ubuntu (installed) Edgy. This is a multi user machine and I have root access. My desktop manager preference is XFCE, however, you apparently cannot set the keyboard layout default in xfce like you can in KDE and Gnome. Everyone else on the machine uses qwerty layout and I use Dvorak.

I can set it manually with 
```
setxkbmap dvorak
```
in a terminal but I want it automated.

---

### Post by ac7ss on 2007-04-01
Still no help?

The plugin for xfce xkb says you can set it in the XF86Config file, but I cannot find it.

---

### Post by Tmi on 2007-04-01
Type it in /etc/xorg.conf instead. XF86Conf is a conf file for an older version of X.

---

### Post by ac7ss on 2007-04-01
> **Tmi said:**
> Type it in /etc/xorg.conf instead. XF86Conf is a conf file for an older version of X.

Yeah, it is set in there, but it won't show up with the applet.

---

