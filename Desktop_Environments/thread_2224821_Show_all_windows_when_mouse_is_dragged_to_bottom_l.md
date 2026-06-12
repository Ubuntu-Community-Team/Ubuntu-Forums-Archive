---
title: "Show all windows when mouse is dragged to bottom left (12.04 Gnome Fallback)"
date: 2014-05-18
forum: Desktop Environments
---

### Post by block g raptor on 2014-05-18
I had Macbuntu installed on my 10.10 machine but since upgrading to 12.04 Ive had manually install all the mac themes and features. Ive got everthing back to  the way my 10.10 looked with the exception of the hotzones (which came included in the Macbuntu package) Basically in 10.0 with Macbuntu installed, Dragging mouse to bottom left would minimise all windows and bottom right would show all windows scaled to fit the screen. is there anyway to achieve this in 12.04 with Gnome fallback desktop ?

---

### Post by varunendra on 2014-05-21
Have you taken a look at CCSM (Compiz Config Settings Manager)? Install it from Software Center / Synaptic, or with -
```
sudo apt-get install compizconfig-settings-manager
```
..then open it from "Preferences" menu or -
press **Alt-F2 >** type **"CCSM" >** press '**Enter**'

Since it has potential to break your desktop settings and window manager, it is recommended to first 'Export' its current settings ("Preferences" in CCSM > Export) so you can restore them by importing the settings file again, if required.

Although I don't know where the 'Minimize all windows' effect is hidden in it, the 'Scale' effect does allow selecting hotzones.

---

