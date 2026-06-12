---
title: "Problem with Xsession / Kiosk mode"
date: 2015-03-02
forum: Desktop Environments
---

### Post by Psycho2481 on 2015-03-02
Hi,

I'm trying to setup Ubuntu 12.04 with a Digital Signage Application in Kiosk Mode. So far I've done great success. But the location of the PC is not the same all the time. So I build up mu Xsession to check for internet acces (by pinging 8.8.8.8, one of Googles DNS Servers) and launching wicd if not accessible.

This works pretty well, but I have no cursor/pointer in wicd. Configuring with the Keyboard works, but other users wont be able to do this...

My /usr/share/xsessions/kiosk.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=Kiosk
Exec=/usr/share/xsessions/kiosk.sh
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

and /usr/share/csessions/kiosk.sh:
```
#!/bin/bash

xset -dpms
( ! ping -c1 8.8.8.8 >/dev/null 2>&1 ) && wicd-gtk --no-tray

while true; do
	cd /opt/path/to/my/app
	./run.sh
	sleep 3s
done
```

Like a mentioned before, this works pretty well. Only the mouse pointer is missing. So if anyone has an idea what I am doing wrong, please help me :D

Other solutions (replacing wicd for example) are welcome to!

Thanks, P

---

