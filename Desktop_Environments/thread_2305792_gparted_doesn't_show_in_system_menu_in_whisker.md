---
title: "gparted doesn't show in system menu in whisker"
date: 2015-12-09
forum: Desktop Environments
---

### Post by Kilarin on 2015-12-09
I'm running Xubuntu 14.04 32bit system on an e555 thinkpad.

I have gparted installed, but I want it to show up in my whisker menu under System.
The odd thing is, when I edit applications, Gparted IS under the whisker System menu.  (and settings)  But when browse the whisker menu normally, it shows up under settings, but NOT under system.

GParted shows "Hide from menus"=OFF  and under Categories has both Settings and System.
So why is it showing up in the "Settings" menu but not under the "System" menu???

---

### Post by Dennis N on 2015-12-09
> **Kilarin said:**
> I'm running Xubuntu 14.04 32bit system on an e555 thinkpad.

I have gparted installed, but I want it to show up in my whisker menu under System.
The odd thing is, when I edit applications, Gparted IS under the whisker System menu.  (and settings)  But when browse the whisker menu normally, it shows up under settings, but NOT under system.

GParted shows "Hide from menus"=OFF  and under Categories has both Settings and System.
So why is it showing up in the "Settings" menu but not under the "System" menu???

The automatic menu generator routine only places entries under one category.
If you want it under 'System' in Whisker Menu, remove 'Settings' from its Categories in the /usr/share/applications/gparted.desktop file. But then it vanishes from the All Settings Window.
I use: **Categories=GNOME;GTK;Settings;HardwareSettings;** and it shows up in 'Settings' on Whisker Menu, and 'Hardware' in the All Settings window (accessible from the bar of Whisker Menu window) which makes sense to me.

---

### Post by Kilarin on 2015-12-09
Ah, one category only.  ok, thank you very much.

---

