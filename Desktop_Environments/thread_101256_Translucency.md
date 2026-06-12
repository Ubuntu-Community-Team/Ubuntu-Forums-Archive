---
title: "Translucency"
date: 2005-12-09
forum: Desktop Environments
---

### Post by manicman on 2005-12-09
hi im trying to enable the transluceny option in the
Kcontrol>windows behavior>transluceny
now i have a ATI 9800 pro card is working well with linux it plays games such as UT2004 and Call of Duty smoothly so i belive that it should be able to handle this when i enable transluceny and reboot i get two error messages one saying i need XOrg that is > 6.8 (i am using Xorg 6.8.2) and another saying add the following to the xorg.conf file:

Section "Extensions"
Option "Composite" "Enable"
EndSection

so after backing up my xorg.conf i added this to my xorg.conf then restarted the xserver when i loged in i didnt get any error messages this time and transluceny was enabled but i was painfully slow i turned it off stright away. after this i found thay all my games either didnt load of where very slow so i decided to see if my graphics card was working.
so i tried $ fgl_glxgears 
and i got the following error
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30
```
now this was working before i edited .xorg.conf and since ive changed it back continues to work so why does adding
Section "Extensions"
Option "Composite" "Enable"
EndSection
stop everything from working ?

---

### Post by pizzach on 2005-12-09
If I remember right it isn't a matter if you're card is fast enough, there just isn't a driver to support it in ati cards yet. Only nvidia.  So your shadows are being done 100% on your CPU.

---

### Post by Naneau on 2005-12-09
this is actually a known bug/feature, you can either enable the hardware acceleration for KDE (or GNOME) OR you can have direct rendering enabled, but never both at the same time. So if you're a gamer, and you want to play games with hardware acceleration (which you obviously do) you'll have to live with the fact that you can get less eye-candy.

---

