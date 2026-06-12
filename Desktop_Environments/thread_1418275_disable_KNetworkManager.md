---
title: "disable KNetworkManager"
date: 2010-02-28
forum: Desktop Environments
---

### Post by genjix on 2010-02-28
This thing has no exit option in it's menu and wireless networks don't show signal strength until you try to connect to them.

Short of purging NetworkManager/KNetworkManager, how can I disable them so they don't start on startup?

Thanks

---

### Post by Frudo on 2010-02-28
Hello there , 
did you try this.?
If you have enabled control center under system menu by editing your menus , there u can find the startup apps.
you can manually edit the startup items there. 
i am sure there is a way to do it in terminal but i donno 
Frudo

---

### Post by genjix on 2010-02-28
thanks but networkmanager isn't under there.

---

### Post by Zorael on 2010-02-28
Hmm.

Try editing **/usr/share/applications/kde4/knetworkmanager.desktop** and comment/remove any lines in there mentioning autostarting. (Comment by prepending the line with a hashmark; **#**.)
```
[Desktop Entry]
Name=KNetworkManager
GenericName=Network Manager
Exec=knetworkmanager
Icon=knetworkmanager
Type=Application
Comment=A KDE frontend for NetworkManager
[COLOR="Red"]**# X-KDE-autostart-after=panel**[/COLOR]
X-KDE-StartupNotify=false
X-KDE-UniqueApplet=true
X-DCOP-ServiceType=Unique
[COLOR="RoyalBlue"]X-KDE-autostart-condition=networkmanagementrc:General:Autostart:true[/COLOR]
Categories=Utility;TrayIcon;System;Applet;

X-Ubuntu-Gettext-Domain=desktop_playground-base
```
The autostart condition line suggests that you may be able to add **Autostart=false** to the **General** section of **~/.kde/share/config/networkmanagementrc** and achieve the same effect. That would make it persist over package upgrades, whereas as soon as you upgrade knetworkmanager the .desktop file will be overwritten and your changes lost.

---

