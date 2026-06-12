---
title: "[Xubuntu] Changing Icon Size in Applications Menu: How?"
date: 2014-04-25
forum: Desktop Environments
---

### Post by ewenss on 2014-04-25
Hi all.

In Xfce 4.10.0, I could easily enlarge the icon sizes in the Applications menu (xfce4-popup-applicationsmenu) by editing $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml and adding this line:

```
<property name="IconSizes" type="string" value="gtk-menu=18,18:gtk-button=18,18:panel-applications-menu=24,24:panel-directory-menu=24,24"/>
```

In Xfce 4.10.1, which is in "trusty," the above has no effect.

I've also tried adding one *or* the other of these lines to my theme's gtkrc file

```
gtk-icon-sizes = "gtk-menu=18,18:gtk-button=18,18:panel-applications-menu=24,24:panel-directory-menu=24,24"
```
OR

```
gtk-icon-sizes = "gtk-menu=22,22:gtk-button=22,22:panel-applications-menu=24,24:panel-directory-menu=24,24:directorymenu-button=22,22:panel-window-menu=32,32"
```

That also has no effect.

I've also tried adding one or the other of the the above lines to $HOME/.gtkrc-2.0

That also has no effect.

I have found this page [http://docs.xfce.org/xfce/xfce4-panel/applicationsmenu](http://docs.xfce.org/xfce/xfce4-panel/applicationsmenu) where it says:

> You can set a custom icon size in gtk-icon-sizes with the name panel-applications-menu. The default icon size is 16px. Special widget name in this plugin is applicationmenu-button.
However, I'm unsure if that does what I am wanting or how to implement it.

Help? Please? I very much need larger icon sizes!

---

### Post by Dennis N on 2014-04-25
If you use the default Whisker Menu (default in Xubuntu 14.04) you can easily change the icon size from its properties dialog for both the categories and the menu items.

---

### Post by ewenss on 2014-04-25
It does, but Whisker Menu does not work for my work flow - I have many programs placed in to sub-menus and need to see them in a glance instead of scrolling.

---

### Post by Toz on 2014-04-26
Hello, me again.
Actually, Trusty has Xfce 4.11.1 On my install those parameters work. Run this command:
```
xfconf-query -c xsettings -p /Gtk/IconSizes -s "gtk-menu=18,18:gtk-button=18,18:panel-applications-menu=24,24:panel-directory-menu=24,24"
```
As I posted over in the Xfce forums, this appears to be broken in Xfce 4.10.1.

---

### Post by ewenss on 2014-04-26
That does effect the directory menu, but in the applications menu everything is still 16x16 pixels. :-\

---

### Post by Toz on 2014-04-26
> **ewenss said:**
> That does effect the directory menu, but in the applications menu everything is still 16x16 pixels. :-\

That's interesting. It affects both for me. You are talking about the original Xfce applications menu plugin thats added to the panel, correct?

---

### Post by ewenss on 2014-04-27
Okay, so I have figured out the problem. Very oddly, it was the index file of my icon them.

This causes the enlarged icons to not be recognized in xsettings:

[24x24/devices]
Size=32
Context=Devices
Type=**Threshold**

This causes it to be recognized:

[24x24/devices]
Size=32
Context=Devices
Type=**Fixed**


Now, one has to have an icon theme that is *utterly comprehensive*, because icons in the Applications menu *do not scale*. Crazy.

---

