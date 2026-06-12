---
title: "Lightdm, x11vnc two seats: VNC keyboard/mouse input only works if seat is active"
date: 2014-02-12
forum: Desktop Environments
---

### Post by Chris312 on 2014-02-12
[COLOR=#000000][FONT=Arial]I have Lightdm setup to run two seats:[/FONT][/COLOR]

[LIST]
[*]XBMC (Seat:0) which uses my monitor
[*]xfce (Seat:1) which uses virtual terminal 8
[/LIST]
[COLOR=#000000][FONT=Arial]This way I can switch between them using Crtl-Alt-F7/F8[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I use x11vnc to connect to display 1 (xfce) via VNC /usr/bin/x11vnc -auth /var/run/lightdm/root/:1 -forever -bg -rfbport 5900 -o /tmp/x11vnc.log -display :1 -xkb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So far so good. I can connect via VNC to xfce but my mouse and keyboard input is not recognized if the display of my server shows XBMC. If I switch to virtual terminal 8 (Ctrl-Alt-F8) using the server keyboard then VNC will work. This is not ideal. I want XBMC to be always be displayed on my monitor and access xfce only via VNC.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]There seems to be some kind of problem which prohibits keyboard/mouse input over VNC if the virtual terminal is not active on the host.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any ideas?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]PS: I used -dk -dp to check if the keyboard and mouse inputs arrive at x11vnc and they do. So that's not the issue. I am using Ubuntu 13.10.

**[B]/etc/lightdm/lightdm.conf**[/B]
```

[COLOR=#222222][FONT=Verdana][LightDM][/FONT][/COLOR][/FONT][/COLOR]
seats=Seat:0, Seat:1

[Seat:0]
autologin-user=zfsmovies
autologin-user-timeout=0
user-session=XBMC


[Seat:1]
greeter-session=lightdm-gtk-greeter
[COLOR=#000000][FONT=Arial][COLOR=#222222][FONT=Verdana]vt=8[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

