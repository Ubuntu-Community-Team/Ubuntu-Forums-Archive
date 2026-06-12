---
title: "debian sid users"
date: 2007-06-21
forum: Debian
---

### Post by kerry_s on 2007-06-21
Becareful of the dhcp3-client and dhcp3-common upgrade, it killed my internet. If you already got caught, what i did was added my debian-etch xfce4 install cd in synaptic and uninstalled the sid ones and installed the ones from the cd.

You been warned. ;)

The lenny update is okay.

---

### Post by webmonkey44 on 2007-06-22
ouch!

---

### Post by kerry_s on 2007-06-22
this problem is all fixed now update away.

another problem popped up for gdm+minimal+flubox users though. the fluxbox update deletes /usr/share/xsessions

the fix
su
mkdir usr/share/xsessions
nano usr/share/xsessions/Fluxbox.desktop

put

[Desktop Entry]
Name=Fluxbox
Exec=/usr/bin/startfluxbox

---

