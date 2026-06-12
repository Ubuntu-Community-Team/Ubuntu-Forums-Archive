---
title: "My Ubuntu has gone ugly"
date: 2012-10-26
forum: Desktop Environments
---

### Post by J&#7885;hn on 2012-10-26
Hi all

I've been messing around with Mate and Xubuntu lately, when I came back to Unity I discovered that most of my windows are borked. The themes aren't being applied and everything looks pretty square and bland.

The only way I can get them working is to launch apps like this:

```
env GTK2_RC_FILES=/usr/share/themes/Radiance/gtk-2.0/gtkrc /usr/bin/firefox
```When I create a new user that seems to work, but I'm curious if I can fix this relatively easily without having to remove all my config files. 

I already tried removing .config and .compiz-1 from my home directory but the problem still remains.

Anyone else seen this? I'm on 12.04LTS 64bit.

Thanks for any suggestions.

---

### Post by Frogs Hair on 2012-10-26
See what file manager is starting in Unity  from help > about and if it is nautilus try the following command. ```
nautilus -q
``` between your three desktops I think you have three file manages and Nautilus is used to draw the desktop in Ubuntu.

---

### Post by J&#7885;hn on 2012-10-29
It is Nautilus but that didn't fix the issue, thanks for replying. Unless I manually specify the GTK2 stuff, everything but the title bar on my windows is beige and boxy.

---

