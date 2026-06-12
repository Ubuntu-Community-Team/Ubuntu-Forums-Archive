---
title: "Lost Panels"
date: 2009-04-09
forum: Desktop Environments
---

### Post by Fernzaty on 2009-04-09
I'm trying the Netbook Remix on my Acer Aspire One and after a couple of weeks of running with the remix desktop, I wanted to try the standard desktop. I used the Switch icon in Preferences, but once it's switch, all I have is the wallpaper, no panels top or bottom, no menu button and no icons. The icons I can deal with but I have no idea why I get no menu and panels, and no idea how to correct this. Can anyone advise please?

---

### Post by x33a on 2009-04-09
try alt+f2 -> gnome-panel.

---

### Post by Lostin60's on 2009-04-10
> **x33a said:**
> try alt+f2 -> gnome-panel.

Same problem. But alt>f2 doesnot work.  If I boot into restore and get a root prompt and try 
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```
I get "--recursive not recognized" I tried it with -R to no avail.  It also tells me 
```
gnome-panels
```
is not a command.  Help...lol.

---

