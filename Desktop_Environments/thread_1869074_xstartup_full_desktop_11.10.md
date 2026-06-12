---
title: "xstartup full desktop 11.10"
date: 2011-10-25
forum: Desktop Environments
---

### Post by tscheff on 2011-10-25
Hi Guys, I'm in a little bit of truble here and don't know how to go on.

Situation is as follows: 
I have a "homeserver" (Ubuntu 11.10) hooked up to a 1920x1080 TV, mostly running xbmc, a mediacenter software in fullscreen. 
What i want to have is a second "virtual" desktop to connect via vnc where I can do some grafical administration stuff.

By now I found out that I'd have to change ~/.vnc/xstartup to
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startx &
```
to get a "full" desktop. But instead im getting this:
[IMG]http://dl.dropbox.com/u/828352/2011-10-25%2013h11_20.png[/IMG]

any advise ?
correct me if I'm wrong but i think gnome3 is not really starting

---

### Post by mburnell on 2011-11-07
Hi tscheff,

I came across your post while I was searching for a solution to the same problem. I was using x11vnc as the server and connecting from a windows machine using putty (to get the port forwarding working) then tightvnc to connect to the gui. My problem was that I wasn't specifying an authority file when starting the x11vnc server, meaning the session was running as a guest (which doesn't have the window manager, etc).

This didn't work for me (gave me the same symptom you've got):

sudo x11vnc -forever -display :0 -usepw

But this worked fine:

sudo x11vnc -forever -auth /var/run/lightdm/root/:0 -display :0 -usepw

(if your auth file isn't in this location, the easiest way to find it would be to log onto the physical box as yourself to get a session going, and use ps wwaux | grep auth).

Hope that helps,

Matt.

---

