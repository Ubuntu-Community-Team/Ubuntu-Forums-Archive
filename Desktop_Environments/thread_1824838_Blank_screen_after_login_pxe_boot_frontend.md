---
title: "Blank screen after login pxe boot frontend"
date: 2011-08-14
forum: Desktop Environments
---

### Post by tpboyce on 2011-08-14
I am trying to setup a PXE boot Mythbuntu frontend.  It boots and brings me to the login screen.  After I login, it brings me to a blank screen with just the mouse pointer.

Here are some logs...

```

/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
ssh-agent is already running
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
env: Thunar: No such file or directory
xfdesktop[1232]: starting up

(polkit-gnome-authentication-agent-1:1240): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files


```

```

[    11.651] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)" (type: KEYBOARD)
[    11.651] (**) Option "xkb_rules" "evdev"
[    11.651] (**) Option "xkb_model" "pc105"
[    11.651] (**) Option "xkb_layout" "us"
[    11.651] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[    11.651] (II) No input driver/identifier specified (ignoring)
[   185.182] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[   185.754] (II) intel(0): EDID vendor "JVC", prod id 16928
[   185.754] (II) intel(0): Using EDID range info for horizontal sync
[   185.754] (II) intel(0): Using EDID range info for vertical refresh
[   185.754] (II) intel(0): Printing DDC gathered Modelines:
[   185.754] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   185.754] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   185.754] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   185.754] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   185.754] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   185.754] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   192.360] (II) AIGLX: Suspending AIGLX clients for VT switch



```

Any help would be greatly appreciated!

---

