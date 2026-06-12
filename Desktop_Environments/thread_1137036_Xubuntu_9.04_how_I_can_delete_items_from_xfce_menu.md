---
title: "Xubuntu 9.04: how I can delete items from xfce menu?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by sitruuna on 2009-04-25
I've just upgraded my Xubuntu from 8.10 to 9.04. One thing is annoying me. There's really much icons in the Applications menu. Especially in the "Settings" menu. 

[[img]http://img70.imageshack.us/img70/8563/screenshota.th.png[/img]](http://img70.imageshack.us/img70/8563/screenshota.png)

There is Xfce 4 Setting Manager but every icon in that is also listed under settings menu. I've found out that I can delete launchers from the menu by deleting them from /usr/share/applications , but if i delete those icons that are listed in both Xfce 4 Settings Manager and under the settings menu, those are not listed in Xfce 4 Settings Manager anymore. I want that those icons are only listed in the Xfce 4 Settings Manager.

I think I should manually edit those launchers in /usr/share/applications . Something in these lines maybe:

```
[...]

Categories=X-XFCE;Settings;DesktopSettings;X-XfceSettingsDialog;
StartupNotify=true
OnlyShowIn=XFCE;
X-XfcePluggable=true

[...]
```

but what? :-s

---

### Post by moycano on 2009-04-25
I was behind something similar: because I didn't like to use the "Add and remove..." application instead of Synaptic, I want to eliminate their launcher from the upper part of the menu (as appear in the 9.04 version of Xubuntu).

I've do it with a ALT+F2 "gksudo mousepad /etc/xdg/xubuntu/menus/xfce-applications.menu" ...and since the file appear to indicate various directories for every submenu, I think their information may result of help.

---

### Post by some_random_noob on 2009-04-25
I used to have trouble with the menus too, which I never sorted out. I don't think that many people here use Xubuntu, so you might want to consider asking the good folks on the Xubuntu IRC or Xubuntu mailing list:

[http://xubuntu.com/help](http://xubuntu.com/help)

---

### Post by sitruuna on 2009-04-26
I figured out a bad way:
```
[...]

Categories=X-XFCE;Settings;DesktopSettings;X-XfceSettingsDialog;
StartupNotify=true
OnlyShowIn=**none**;
X-XfcePluggable=true

[...]
```

I did this to all icons that are listed in the Xfce 4 Settings Manager, and now those are only listed in there. :)

---

