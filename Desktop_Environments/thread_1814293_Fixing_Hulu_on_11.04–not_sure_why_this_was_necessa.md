---
title: "Fixing Hulu on 11.04–not sure why this was necessary"
date: 2011-07-29
forum: Desktop Environments
---

### Post by bturrie on 2011-07-29
I happened to try Hulu this morning in the process of testing Swiftfox which I had just installed. Hulu said I needed to download a new Flash Player, but the minimum version it said I needed was less recent than the one I had installed. Poking around I found that /var/lib/flashplugin-installer had npwrapper.libflashplayer.so which I believe is an older 32bit flashplugin.

cp /usr/lib/flashplugin-installer/libflashplayer.so /var/lib/flashplugin-installer/libflashplayer.so

corrected the problem. Hulu is now working on my system.

---

### Post by bturrie on 2011-07-29
BTW this was a fresh Natty install a few weeks ago. It was not an upgrade. During the install process I believe I remember seeing the flash-plugin installation.

---

