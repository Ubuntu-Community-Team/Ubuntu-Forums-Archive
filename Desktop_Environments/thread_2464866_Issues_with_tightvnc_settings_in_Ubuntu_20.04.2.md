---
title: "Issues with tightvnc settings in Ubuntu 20.04.2"
date: 2021-07-14
forum: Desktop Environments
---

### Post by itsshowtime on 2021-07-14
Hi all,
 
I initially followed this guide to get VNC access to my Ubuntu VM: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04).
 
I had to change my client to connect over port 5901 instead of 5900 and I don't seem to be able to open the vncserver on the default 5900 as the -httpport option doesn't work at al???... Currently it looks like **vncserver randomly picks a port in the 590x range** and increments, even though I always close my sessions...
 
After changing the client to the random dynamic port vncserver is listening to, I received an **empty grey window**.
 
Some googling brought me to: [https://askubuntu.com/questions/800302/vncserver-grey-screen-ubuntu-16-04-lts](https://askubuntu.com/questions/800302/vncserver-grey-screen-ubuntu-16-04-lts) where the following line: **'nautilus &' made it possible for me to see and interact with a single application window 'Files'** but still nothing more. Opening Terminal from Files works in the background. However, like any other application, Terminal stays invisible within the VNC client (it opens on the VMWare client though).
 
Currently, I removed all other configuration within the .vnc/xstartup file and the content looks as follows:
```

#!/bin/sh
 
#xrdb $HOME/.Xresources
#startxfce4 &
 
#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
 
#xsetroot -solid grey
#vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
 
#gnome-panel &
#gnome-settings-daemon &
#metacity &
 
nautilus &
 
#Fix to make GNOME work
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession

```

---

### Post by ActionParsnip on 2021-07-14
What are you wanting to do on the remote system once connected via VNC? Why do you need the full desktop?

---

