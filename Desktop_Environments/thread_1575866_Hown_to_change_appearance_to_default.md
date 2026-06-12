---
title: "Hown to change appearance to default?"
date: 2010-09-16
forum: Desktop Environments
---

### Post by rudysuryanto on 2010-09-16
:lolflag:When I type :
 sudo cp /usr/share/applications/gnome-appearance-properties.desktop

in terminal, then I reboot, I have different appearance in desktop, there is no main menu, there is no icon, there is no panel, How Should I do to reset it to default? Thank's

---

### Post by hrickh on 2010-09-16
> **rudysuryanto said:**
> :lolflag:When I type :
 sudo cp /usr/share/applications/gnome-appearance-properties.desktop

in terminal, then I reboot, I have different appearance in desktop, there is no main menu, there is no icon, there is no panel, How Should I do to reset it to default? Thank's
In your home directory, type this: rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Log out, then back in. You should see everything reset.

R.
==

---

