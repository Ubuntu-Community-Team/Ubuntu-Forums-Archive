---
title: "Unable to share uBuntu 14.04 desktop frm Windows 7 using Tight VNC"
date: 2015-04-03
forum: Desktop Environments
---

### Post by Rajeev_Sikka on 2015-04-03
Hi,

I am on uBuntu 14.04. Am trying to access it from my Windows 7 machine using Tight VNC.

I read various articles on the internet and made progress but am now stuck. 
When I VNC, I see a grey area with 1 terminal window. Here is how my ./vnc/xstartup looks like:

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

Appreciate any answers.

Thanks
Rajeev

---

