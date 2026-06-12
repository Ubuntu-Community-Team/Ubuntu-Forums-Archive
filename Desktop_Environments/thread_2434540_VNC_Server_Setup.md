---
title: "VNC Server Setup"
date: 2020-01-07
forum: Desktop Environments
---

### Post by kapsiakchris on 2020-01-07
I am running lubuntu 19.10 and am trying to get vnc server up and running using tightvncserver. So far at best from the vnc connection I get a new desktop environment, not viewing what is on the pc, along with no taskbar bar. Below is the content of my xstartup

#!/bin/bash

xrdb $HOME/.Xresources
startlxqt &


and here is the content of my vncserver@.service
[Unit]
Description=Remote desktop service (VNC)
After=syslog.target network.target

[Service]
type=forking
User=XXX
PIDFile=/home/xxx/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart =/usr/bin/vncserver -depth 24 geometry 1280x800 :%i
ExecStop =/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target

---

