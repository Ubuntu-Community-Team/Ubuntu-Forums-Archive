---
title: "Gnome 3 on Natty or other versions install"
date: 2011-04-28
forum: Desktop Environments
---

### Post by zzzz401 on 2011-04-28
in terminal type these commands 

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
Afterward go into your login screen and there should be a box saying Ubuntu scroll down on it and pick Gnome. 
(**NOTE** do not have system programs or apps running it will cause install to fail.)

I tried this out works perfectly.
:grin::grin::grin:

---

### Post by jakslev on 2011-04-28
Didn't work for me - ended up with an odd flickering screen under GNOME3...

---

### Post by Furyhunter on 2011-04-28
It worked, but it messes up GDM's theming, as well as the Gnome Shell theme...

---

### Post by slooksterpsv on 2011-04-28
> **Furyhunter said:**
> It worked, but it messes up GDM's theming, as well as the Gnome Shell theme...

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

Reboot and that should fix that issue.

---

### Post by itisbasi on 2011-04-30
@slooksterpsv double thumbs up for your signature..

---

