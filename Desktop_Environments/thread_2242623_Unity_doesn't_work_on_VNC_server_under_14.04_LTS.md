---
title: "Unity doesn't work on VNC server under 14.04 LTS"
date: 2014-09-03
forum: Desktop Environments
---

### Post by kevin109 on 2014-09-03
After upgrading to Ubuntu 14.04 LTS, I find the Unity destkop in vnc4server never works as it did under Ubuntu 12.04 LTS.


Here is my ~/.vnc/xstartup for vnc4server:


[FONT=courier new]    #!/bin/sh[/FONT]
[FONT=courier new]    [/FONT]
[FONT=courier new]    xrdb $HOME/.Xresources[/FONT]
[FONT=courier new]    xsetroot -solid grey[/FONT]
[FONT=courier new]    [/FONT]
[FONT=courier new]    /usr/bin/gnome-session &[/FONT]


That works fine starting Unity desktop on Ubuntu 12.04 LTS, but unfortunately on 14.04 LTS only a gray screen is seen in vncviewer.


I searched a little and find [this article]("http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html") shows the way to start legacy gnome desktop (gnome-fallback) in vnc on 14.04, but what I want is the solution for a normal Unity desktop in vnc.


Has anyone successfully run Unity desktop in a vnc session (vnc4server, or any other vnc server) on Ubuntu 14.04 LTS?

---

