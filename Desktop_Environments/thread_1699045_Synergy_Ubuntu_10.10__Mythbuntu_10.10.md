---
title: "Synergy Ubuntu 10.10 / Mythbuntu 10.10"
date: 2011-03-03
forum: Desktop Environments
---

### Post by PhonicLynx on 2011-03-03
Strange problem here. If I use QuickSynergy I can get the two computers to connect correctly with no problems.. its just a pain to have to connect each comptuer every time. One computer doesn't have a keyboard or a mouse so I have to VNC to it.

Now I've followed the SynergyHowTo on connecting the computers but it seams the Mythbuntu computer freezes using the script. However the Ubuntu 10.10 has no problems.

_**/etc/gdm/Init/Default**_
```
/usr/bin/killall synergyc
while [ $(pgrep -x synergyc) ]; do sleep 0.1; done
/usr/bin/synergyc 192.168.0.110>
```
If I insert that code into the startup script and reboot the computer on startup GDM stops. Synergy connects correctly because I can move to the other screen using the server. However ice doesn't load nor does mythfrontend.

If I run "*sudo service gdm restart*" ice starts. If i run that command again i get mythfrontend to start. Kinda got me baffled.

If I take that config out of the Default script mythfrontend starts but I still need to start Synergy using a SSH command.

Any Ideas?

---

