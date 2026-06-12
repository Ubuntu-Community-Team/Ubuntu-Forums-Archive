---
title: "Help debugging kmail tray applet"
date: 2010-06-10
forum: Desktop Environments
---

### Post by 67GTA on 2010-06-10
Running 10.04 with KDE 4.4.4 from ppa repo. This problem existed before  updating to 4.4.4. I select the option to have kmail start in the system  tray at boot. For some reason it doesn't. Once I manually start kmail,  the tray applet appears. I just moved from Opensuse 11.2, and didn't  have this bug. I formatted my /home partition, so it has to be a local  bug. Where can I look to try and find the cause? Systemsettings>Advanced>Autostart contains blueman-applet and qtcurve script, and  /home/user/.kde/Autostart is empty.  /home/user/.kde/share/config/kmailrc shows:

SystemTrayEnabled=true
SystemTrayPolicy=ShowAlways
UseMessageIndicator=true
beep-on-mail=true
checkmail-startup=true

---

