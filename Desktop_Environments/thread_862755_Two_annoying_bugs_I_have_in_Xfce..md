---
title: "Two annoying bugs I have in Xfce."
date: 2008-07-17
forum: Desktop Environments
---

### Post by kaldor on 2008-07-17
Xubuntu 8.04

1) Sound won't work anymore. The volume icon won't appear, and it is stuck on one volume setting. I can't re add the icon either.

2) Sometimes Xubuntu won't load up. I log in, and it just stays on the grey screen and I need to reboot. KDE and Gnome work fine.

---

### Post by kaldor on 2008-07-18
Still having this problem, need help.

---

### Post by coffeecat on 2008-07-18
> **kaldor said:**
> 2) Sometimes Xubuntu won't load up. I log in, and it just stays on the grey screen and I need to reboot. KDE and Gnome work fine.

I came across this fix on the Linux Format forum. It was specifically to do with the same problem that occurred when trying to log into Xubuntu in the special Ubuntu that LXF did on a recent DVD - a gnome/kde/xfce Ubuntu multidesktop affair. Whether the bugfix was specific to the LXF special or whether this is a bug in Ubuntu generally, I don't know. But it's worth trying.

Log into Gnome and edit /usr/share/xsessions/xfce4.desktop. Here's the offending line (now commented out) and the one you need to put in instead:

```
#Exec=startxfce4
Exec=xfce4-session
```Then log out of Gnome and log into Xfce.

---

### Post by DkkD on 2008-07-18
> **kaldor said:**
> Xubuntu 8.04
1) Sound won't work anymore. The volume icon won't appear, and it is stuck on one volume setting. I can't re add the icon either.


Open the terminal and enter: xfce4-mixer

I guess something could be muted or something like that.

---

