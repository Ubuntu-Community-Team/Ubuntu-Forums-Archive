---
title: "How to make a Unity launcher for Spread Mode?"
date: 2016-04-28
forum: Desktop Environments
---

### Post by unflavored on 2016-04-28
I'm running 16.04. I want to click on a Unity launcher that invokes Super+W, or spread mode. [Last I saw this answered was in 11.04.](https://askubuntu.com/questions/33852/can-unity-display-a-launcher-icon-for-spread-mode) Is there anything that works in 16.04, preferably without installing more software?

---

### Post by mc4man on 2016-04-29
Nothings really changed there, basically that ask ubuntu deal except it's not necessary to create a script or link. You do have to install xdotool, then just create a .desktop in .local/share/applications & drag onto the unity launcher. It's best (or possibly needed ) to give it an icon.

basic example - 
```
[Desktop Entry]
Version=1.0
Name=Spread
Type=Application
Exec=xdotool key super+w
Icon=/home/doug/Pictures/arrow1.png
```

Launchers such as this can only be used about once every 7 sec.'s or so, eg. when the icon stops flashing

---

### Post by unflavored on 2016-05-11
Thank you, mc4man.

---

### Post by mc4man on 2016-05-12
just in case someone wants & can't find a decent icon, attached 2 I have, different colors, work ok in launcher as having trans backgrounds

---

### Post by unflavored on 2016-05-18
Thanks, I altered one of those.

---

