---
title: "Building dedicated box for emulation"
date: 2014-12-18
forum: Gaming &amp; Leisure
---

### Post by Amon_Re on 2014-12-18
Hi guys,

I'm currently trying to setup a (minimal) system with the sole purpose of running [EmulationStation]("http://emulationstation.org/"). Getting EmulationStation up & running was a breeze and everything is working fine. Now I want to log directly into the application and I'm stuck. I can't get the joystick to work in the app while it does work in the terminal (tested with jstest).

Here's what I did, I created a custom.desktop file in /usr/share/xsessions with the following contents:
```
[Desktop Entry]
Name=EmuStation
Comment=EmuStation
Exec=/usr/bin/emulationstation
X-Ubuntu-Gettext-Domain=<gnome-session-3.0>
```

I can log into the app directly if I select this instead of Ubuntu but at this point I can't use the joystick (even though the app sees it).
Logging out & back in with the Ubuntu desktop, the application works normally.

When Ubuntu is initializing it's desktop it must be doing *something* to make it work but I can't seem to find out what :( 
This is all using Ubuntu 14.10.

---

### Post by pqwoerituytrueiwoq on 2014-12-18
been there done that
your issue is ES requires a window manager, if you start xfwm4 or openbox before starting ES it will work

as a result i start a minimal lubuntu install and put it on start-up and remove the panel
[http://imgur.com/gallery/1QvjA](http://imgur.com/gallery/1QvjA)

if you are making your own xsession you will need a window manger, emulationstation, and pulseaudio running

---

