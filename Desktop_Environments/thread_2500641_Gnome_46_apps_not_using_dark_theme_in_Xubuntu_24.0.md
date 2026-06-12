---
title: "Gnome 46 apps not using dark theme in Xubuntu 24.04.1"
date: 2024-09-07
forum: Desktop Environments
---

### Post by mku2024 on 2024-09-07
When selecting a dark theme like Greybird-dark or Adwaita-dark in Xubuntu's Appearance setting, 
Gnome 46 applications do not use the dark-theme and appear in light mode.

Xubuntu 24.10 (Oracular Oriole) Daily Build dark theme works,
but Xubuntu 24.04.1 (Noble Numbat) dark mode doesn't work for the following apps:
- App Center
- Firmware Updater
- Document scanner
- Disk Usage Analyzer
- Sudoku
- Fonts

---

### Post by coffeecat on 2024-09-07
Support, not chat. *Thread moved to **Desktop Environments**.*

---

### Post by Dennis N on 2024-09-07
Many of the Gnome Applications use **libadwaita**, so gtk3 themes will not work with these.
[https://apps.gnome.org/](https://apps.gnome.org/)
I imagine those still using gtk3 will be upgraded to libadwaita in due time.

---

