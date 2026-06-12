---
title: "Changing Nautilus behavior for MTP mounts in 13.10"
date: 2014-02-07
forum: Desktop Environments
---

### Post by timothy-russ on 2014-02-07
I have an Android phone that mounts on connect as an MTP instance and automatically opens a window to view the contents of the Flash and SD card. I'm ecstatic that it mounts without any intervention, but I'd much prefer that it not open any sort of window each time I plug it in. Searching through the media/connection settings in the system properties, I don't see any that appear to relate to an MTP device like an Android phone - in fact, all the entries listed there are set to prompt for the desired action.

Anyone know any config file changes that might accomplish suprpessing the auto-open of that MTP device window?

---

### Post by mc4man on 2014-02-07
You would need to edit your  gsettings as in screen, either in dconf-editor or thru a gsetting/dconf command
```
gsettings set org.gnome.desktop.media-handling automount-open false
```
(I actually disable both options but for your purpose the automount-open is the one to disable

---

