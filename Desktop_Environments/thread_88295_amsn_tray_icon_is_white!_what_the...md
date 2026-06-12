---
title: "amsn tray icon is white! what the..?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Yoda_Oz on 2005-11-09
just installed amsn and the tray icon is white. when i used to have it installed on gnome the icons where like the proper colour like in windows' version. now in kde i dont know whats going on!
Is there some sort of compatibility issue here? i cant seem to find anything on this on google. only stuff about the backgrounds of the icons being not the same colour as the taskbar (which is nothing to do with my problem)..

any help apprec.!

---

### Post by f1dave on 2005-11-09
I had a similar problem when I installed amsn a while back. Then I got tired of its tcl/tk interface anyway, and switched to kopete.

---

### Post by thrust on 2005-11-10
just right click on the tray icon and click properties to change it, the icon is in /usr/share/amsn/icons/48x48  if u installed aMSN from kynaptic. click "other icons and then click browse to get to that dir. the same thing happend to me with BMP and and i couldn't find the icon, that might be your problem. but the icon should be in that dir so u can jis change it. i dont really know why it happens, its weird

---

### Post by Yoda_Oz on 2005-11-10
i cant right click on the tray icon. if i do that then i get the amsn menu. is there any other way of accessing the icon properties of a tray icon?

---

### Post by thrust on 2005-11-10
i figured out a way to fix your problem, go to "/usr/share/applications" and edit amsn.desktop as root, in kate, then replace "Icon=msn.png" with "Icon=/usr/share/amsn/icons/48x48/msn.png"
and then logout and log back in and the icon should be there.

hope this werks, it werked fer me, the file should look like this

[Desktop Entry]
Name=aMSN
Exec=amsn
Icon=/usr/share/amsn/icons/48x48/msn.png
Info=AMSN
Categories=Application;Network;
Comment="MSN Messenger for Linux"
Comment[fr]="MSN Messenger pour Linux"
Comment[de]="MSN Messenger fr Linux"
Comment[nl]="MSN Messenger voor Linux"
Comment[no]="MSN Messenger for Linux"
Terminal=0
Type=Application

---

