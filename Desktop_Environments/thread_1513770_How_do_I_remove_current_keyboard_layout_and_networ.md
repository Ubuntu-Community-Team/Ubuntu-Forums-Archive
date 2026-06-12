---
title: "How do I remove current keyboard layout and network status from notification area?"
date: 2010-06-20
forum: Desktop Environments
---

### Post by Somnum on 2010-06-20
They are of no use to me and only take up space on an already cluttered panel. How do I get rid of them without removing the notification area itself?

---

### Post by technocp on 2010-06-20
> **Somnum said:**
> They are of no use to me and only take up space on an already cluttered panel. How do I get rid of them without removing the notification area itself?
right click on the object and select remove from panel

---

### Post by Somnum on 2010-06-20
> **technocp said:**
> right click on the object and select remove from panel
Naturally, there is no such option for either of them.

---

### Post by simosx on 2010-06-20
If you have more than one keyboard layout enabled, then you get the keyboard indicator automatically on the notification area. If you can live with one keyboard layout, then the indicator will go. There might be a way, using gconf-editor, to get these not appear in the notification area. I did not try it and I would welcome feedback whether you found a solution or not.

---

### Post by menesis on 2010-09-15
See [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/519372](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/519372) for a command to disable the keyboard icon.

---

### Post by oldmankit on 2010-12-09
There was a fix which no-longer works for maverick. The new(er) bug is here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/631989](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/631989)

---

### Post by Krytarik on 2010-12-10
Hope you get the message after such a long time.:-?

To disable the keyboard-layout-indicator, enter in a terminal:
```
gconftool-2 -s /desktop/gnome/peripherals/keyboard/general/disable_indicator -t bool true
```To disable the network-indicator:
untick "Network Manager" in "System -> Preferences -> Startup Applications".

Both work for me, I'm also running 10.04.

---

### Post by oldmankit on 2010-12-10
> **Krytarik said:**
> Hope you get the message after such a long time.:-?

To disable the keyboard-layout-indicator, enter in a terminal:
```
gconftool-2 -s /desktop/gnome/peripherals/keyboard/general/disable_indicator -t bool true
```To disable the network-indicator:
untick "Network Manager" in "System -> Preferences -> Startup Applications".

Both work for me, I'm also running 10.04.

I think that this is the fix mentioned in the first bug but that it's no-longer working in 10.10 (the second bug).

---

