---
title: "Unknown Error in Gnome Config Editor"
date: 2006-07-16
forum: Desktop Environments
---

### Post by cajunaggie on 2006-07-16
I went into the gconf to add some desktop icons. I opened a key called computer_icon_name on accident. When I closed it, it gave me the following error message > "An error occured while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly."
In addition the value changed from <no value> to 0. I tried to switch it back but it won't let me. The computer icon displays itself but there's no name displayed underneath? Suggestions?:confused:

---

### Post by ayoli on 2006-07-16
you can restore it with this command in a console:
```
gconftool-2 --unset /apps/nautilus/desktop/computer_icon_name
```
assuming this is the location of the key you change, however replace it with the right location. if it doesnt work try:
```
gconftool-2 --recursive-unset /apps/nautilus/desktop/
```
regards.

---

