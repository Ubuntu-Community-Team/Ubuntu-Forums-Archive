---
title: "Network in LXDE"
date: 2009-05-15
forum: Desktop Environments
---

### Post by pointyblue on 2009-05-15
Hi,

I just installed LXDE on my Xubuntu 904-netbook.

Wifi works fine in an XFCE session but I can't figure out how to connect to the network when I'm in an LXDE session.

Any ideas?

:)

---

### Post by kerry_s on 2009-05-15
is xubuntu using network-manager?

try pressing alt+f2 and type> nm-applet

---

### Post by pointyblue on 2009-05-15
Ok, so I figured out how to connect to the network: Run->nm-applet

But I have to do it manually every time - it doesnt just connect autamatically like it would in an xfce-session or when running Ubuntu.

How do I make it run automatically when I boot the machine?

Btw: Thanks Kerry.

---

### Post by tonytraductor on 2009-05-15
This might be helpful:
[http://forum.lxde.org/viewtopic.php?t=111&f=8](http://forum.lxde.org/viewtopic.php?t=111&f=8)

You can autostart by adding to:
/etc/xdg/lxsession/LXDE/autostart

A less global way would be to make a *.desktop file in the ~/.config/autostart folder. 
Something like:
    [Desktop Entry]
    Encoding=UTF-8
    Version=0.9.4
    Type=Application
    Name=nitrogen
    Comment=
    Exec=nitrogen --restore
    StartupNotify=false
    Terminal=false
    Hidden=false

Well, except in this case, it just shows running nitrogen to restore your wallpaper.

---

### Post by pointyblue on 2009-05-15
I added nm-applet to /etc/xdg/lxsession/LXDE/autostart and now it loads as it should.

Thanks! ):P

---

