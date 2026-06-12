---
title: "Low monitor resolution"
date: 2006-09-12
forum: Desktop Environments
---

### Post by alekz on 2006-09-12
Hi guys, i got a  Insignia™ 27" Widescreen Flat-Panel LCD HDTV and i connect my pc to it, the problem is that on ubuntu i can only reach 640*480 as maximun resolution and on windows i have 1024*768, so how can i have 1024*768 on ubuntu Dapper?

Thanks.

---

### Post by mssever on 2006-09-12
Try looking in /etc/X11/xorg.conf for the section that lists resolutions, and add the monitor's native resolution to it (after backing up xorg.conf). Then, logout and kill X (press Ctrl+Alt+Backspace). When everything comes back up, you should be able to select the resolution you added.

---

