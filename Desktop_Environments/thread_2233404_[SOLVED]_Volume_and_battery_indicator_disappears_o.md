---
title: "[SOLVED] Volume and battery indicator disappears on xubuntu 14.04"
date: 2014-07-08
forum: Desktop Environments
---

### Post by gian_nuke on 2014-07-08
Hi,
volume and battery (I'm on a Samsung Serie 5 laptop) indicators disappear without apparent cause...

Anyone can guide me on how to check and eventually re-enable them?
Thanks in advance... :)

---

### Post by Toz on 2014-07-08
Make sure the "Indicator Plugin" is added to the Panel. If it is already added, try removing and re-adding it. If the problem persists, you may find helpful debug information in the ~/.cache/upstart/startxfce4.log file.

---

### Post by gian_nuke on 2014-07-08
> **Toz said:**
> Make sure the "Indicator Plugin" is added to the Panel. If it is already added, try removing and re-adding it. If the problem persists, you may find helpful debug information in the ~/.cache/upstart/startxfce4.log file.

Adding "Indicator Plugin" to the panel works!

In details: right click on the panel, *Panel* > *Add New Elements*, than search for *Indicator Plugin* and add it!

Thank you Toz! :D

---

