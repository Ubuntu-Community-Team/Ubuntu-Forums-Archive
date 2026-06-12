---
title: "Boot directly to XBMC session (always)"
date: 2014-02-01
forum: Desktop Environments
---

### Post by Peco.peco on 2014-02-01
Hello
Please, how configure my Lubuntu to boot directly in to XBMC session? I changed [COLOR=#ff0000]/etc/lightdm/lightdm.conf[/COLOR] and it doesn't work.

[COLOR=#0000ff][SeatDefaults]
autologin-guest=false
autologin-user=htpc
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=XBMC[/COLOR]

XBMC session is OK, works[COLOR=#ff0000]
/usr/share/xsessions/XBMC.desktop[/COLOR]
[COLOR=#0000ff][Desktop Entry]
Name=XBMC
Comment=This session will start XBMC Media Center
Exec=xbmc-standalone
TryExec=xbmc-standalone
Type=Application[/COLOR]

Lubuntu boots _always to last_ used session. I want boot _alway to XBMC_ session.
Thanks!

---

### Post by SuperFreak on 2014-02-01
Not sure about Lubuntu but I boot straight to XBMC on my 13.10 Ubuntu machine. I just put an entry in "StartUp Applications" for XBMC ( I think for command I put the /usr/bin/ location for XBMC

---

### Post by Peco.peco on 2014-02-05
Yes, it works. But I would like boot directly to XBMC session without start desktop.

---

### Post by SuperFreak on 2014-02-05
This probably isn't what you are after, but I have XBMC maximized on last shutdown so none of the desktop shows. Then when I reboot XBMC is full screen and desktop is hidden.

edit:  perhaps you should consider XBMCubuntu

---

### Post by Peco.peco on 2014-02-06
I don't like XBMCbuntu. A lot of things missing there. XBMCbuntu can always boot to XBMC session (doesn't matter on last used session). But I don't know how it possible. I don't know where is this configuration.

---

