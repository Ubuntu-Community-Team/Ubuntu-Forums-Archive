---
title: "How can I improve remote login performance?"
date: 2007-04-23
forum: Desktop Environments
---

### Post by FoolsGold on 2007-04-23
I'm testing out a server I built by attempting to remote login to it, but the desktop performance is pretty poor. I've tried XDMCP and Gnome Remote Desktop so far, and I know there are techniques such as disabling the desktop wallpaper and running with few (if any) effects, but are there any other things I can do to improve performance? With XDMCP particularly, the fade effect from clicking the shutdown button or running a gksu-ed app causes a very long pause as the desktop attempts to fade.

Should I be using a different remote desktop client? Haven't tried VLC server yet, just the built in stuff.

---

### Post by Slim Odds on 2007-04-23
> **FoolsGold said:**
> I'm testing out a server I built by attempting to remote login to it, but the desktop performance is pretty poor. I've tried XDMCP and Gnome Remote Desktop so far, and I know there are techniques such as disabling the desktop wallpaper and running with few (if any) effects, but are there any other things I can do to improve performance? With XDMCP particularly, the fade effect from clicking the shutdown button or running a gksu-ed app causes a very long pause as the desktop attempts to fade.

Should I be using a different remote desktop client? Haven't tried VLC server yet, just the built in stuff.

Is there something wrong with your LAN?

Mine works fine on my 100Mb network.

---

### Post by FoolsGold on 2007-04-23
> **Slim Odds said:**
> Is there something wrong with your LAN?

Mine works fine on my 100Mb network.

No, though I am connecting to a wireless connection which does a (theoretical) max of 54 Mb.

Doesn't matter anyway, found out something called "FreeNX" which looks good.

---

### Post by Jhongy on 2007-04-24
I tried over 802.11b, painfully slow. 

What I want to know is though, how did you manage to log into Gnome via XDMCP? I only could get into KDE or xfce... Gnome just hung with a liuttle box in the corner when loading.

---

### Post by FoolsGold on 2007-04-24
> **Jhongy said:**
> I tried over 802.11b, painfully slow.
Ah, at least I'm not the only one then. :)

Compression is definitely something to look into I think.

> What I want to know is though, how did you manage to log into Gnome via XDMCP? I only could get into KDE or xfce... Gnome just hung with a liuttle box in the corner when loading.
I just went into Preferences -> Login Window (or some other similar menu combination), selected the "Remote" tab and chose Plain. Least amount of bandwidth to use since the background didn't need to be rendered.

---

### Post by Slim Odds on 2007-04-24
> **Jhongy said:**
> I tried over 802.11b, painfully slow. 

Well, 802.11b is only 11Mb

I use it with 802.11g with works just fine at 54Mb. Full graphical login, no problems.

---

### Post by Slim Odds on 2007-04-24
> **FoolsGold said:**
> I just went into Preferences -> Login Window (or some other similar menu combination), selected the "Remote" tab and chose Plain. Least amount of bandwidth to use since the background didn't need to be rendered.


Just don't forget to restart GDM. I sometimes forget that when I install a new machine and then I wonder why it won't connect.

---

### Post by nothing on 2007-04-24
Im still using edgy vnc4server.... I tried remote desktop in Feisty and it was unusable for me... on my LAN or over the Internet...

---

