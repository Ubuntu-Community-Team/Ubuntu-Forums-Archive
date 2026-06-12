---
title: "removing Ubuntu's default menu bar at the top"
date: 2011-10-17
forum: Desktop Environments
---

### Post by hamid.afshar on 2011-10-17
How can i remove the bar in the screenshot that I have attached to this post. It is really annoying me. just to let you know that i cant right click on it. And it is not gnome-panel.

Please help me if you can as this is really getting in my way. Even if i install gnome-shell (Another window manager) this still gets in the way of that and you end up with a confused bar at the top which looks like a rainbow.

The interesting thing also is that when i do:

[HTML]gnome-shell[/HTML]In terminal it says that there is already a window manager at work so please use the -replace option. (paraphrased)

Help!!!! 8-|

---

### Post by mcduck on 2011-10-17
The correct way to switch to gnome-shell would be selecting it as your session form the login screen. That should also avoid the problem you are having.

(And yes, requiring the "--replace" option when switching a window manager is absolutely normal, you already have one running so you need to tell the new one to unload the old one and replace it, instead of trying to run at the same time)

If you sue a transparent gnome-shell them you might still see a menu behind the gnome-shell's top panel. There are two ways to solve that, you can wither disable the global menu (which would of course screw Unity session pretty badly) or use dconf-editor or gnome-tweak-tool to disable Nautilus from managing your desktop (which means loosing desktop icons and right-click menu).

---

