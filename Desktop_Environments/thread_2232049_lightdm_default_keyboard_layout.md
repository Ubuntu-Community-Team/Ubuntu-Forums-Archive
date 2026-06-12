---
title: "lightdm default keyboard layout"
date: 2014-06-29
forum: Desktop Environments
---

### Post by Thomas_Jrvstrand on 2014-06-29
Hi!

I've just installed Ubuntu 14.04 and added a custom keyboard layout (called custom). Now I have two issues that may or may not be related.
1. My keyboard layout is addable through the normal text entry dialog, and shows up in the list of layouts in the gnome-panel applet, but it is grayed out. I can select the layout and it seems to work fine, I'm just curious why it's grayed out, seems it should indicate some sort of problem? 

I can't seem to find where I should look for any problems related to the layout either

```
setxkbmap -layout custom
``` works fine with no errors

when adding the layout, /var/log/Xorg.0.log just says:
```
[  1058.827] (II) XKB: generating xkmfile /var/lib/xkb/server-552896C96CC84BB8AF5014E4CACE61606E9CE964.xkm
``` with no errors

I have added my layout by:
- adding the file /usr/share/X11/xkb/symbols/custom
- Adding my layout to /usr/share/X11/xkb/rules/evdev.xml and evdev.lst
- Adding settings to /etc/default/keyboard and running dpkg-reconfigure keyboard-configuration

What am I missing?

2. lightdm doesn't want to remember my default keyboard layout selection so I always have to change it before typing in my password.

Any help appreciated!

BR,
Thomas

---

