---
title: "mounts not visible on desktop"
date: 2011-10-13
forum: Desktop Environments
---

### Post by EikeB on 2011-10-13
Hi there, i just Updates to ubuntu 11.10 and have one little problem remaining. There are no more icons of the mounted devices on my desktop . In 11.04 there was a configuration in gconf-editor that was called apps/nautilus/desktop/mounts_visible and was set to true. In 11.10 there is no such configuration value. Is it not longer possible in the new ubuntu version or do I have to configure it somewhere else?

---

### Post by mc4man on 2011-10-13
The option is enabled in gsettings by default but not 'working' so to speak

So a couple of ways. may be others
If you install dconf-tools, then run dconf-editor you can navigate to where I show in screen (expand the 'org' section > nautilus > ect.
Disable, then re-enable the option, volumes will start showing up

Or run these 2 commands - 
```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```
```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

---

### Post by crdlb on 2011-10-13
The option is now in dconf-editor, at org.gnome.nautilus.desktop. In a quick test, it doesn't seem to be working for me though.

Edit: toggling it works for me too; that's very odd.

---

### Post by EikeB on 2011-10-14
Thanks for your answers, I will try it later.

---

### Post by robert shearer on 2011-10-14
> **mc4man said:**
> The option is enabled in gsettings by default but not 'working' so to speak
 run these 2 commands - 
```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```
```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

Magic !.. this has been bothering me for weeks.
Thanks a bunch for the fix. 

cheers, Bob.

---

### Post by EikeB on 2011-10-14
Worked for me too, thanks :)

---

### Post by merlinus on 2011-10-24
These workarounds will not do anything for me unless file manager is set to manage the desktop in the gnome tweak tool.

---

### Post by crdlb on 2011-10-24
> **merlinus said:**
> These workarounds will not do anything for me unless file manager is set to manage the desktop in the gnome tweak tool.

Is that unexpected? Nautilus is how icons are drawn on the desktop, including those for mounted volumes.

---

### Post by Jayyin11043 on 2011-10-24
would that affect how desktop icons are arranged on the desktop because every  time I restart my computer the icons all get crammed into the left side of my desktop

---

