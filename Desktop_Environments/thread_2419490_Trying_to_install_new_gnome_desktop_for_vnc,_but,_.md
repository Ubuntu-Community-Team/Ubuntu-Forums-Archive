---
title: "Trying to install new gnome desktop for vnc, but, stuck with gray screen"
date: 2019-05-22
forum: Desktop Environments
---

### Post by lk1234 on 2019-05-22
Hi,

I installed gnome desktop:
```
apt-get install ubuntu-gnome-session gnome-shell
```

Modified the ~/.vnc/xstartup file to the following:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc
gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &
```

[LIST]
[*]I closed vnc viewer, and opend it again.. it was still on xfce desktop.
[*]So, I tried "Log out" in Vnc Viewer on the xfce desktop, and tried logging back in to see if it now picks up the new gnome desktop.
[*]But now, all i get is a blank gray screen - no icons, no nothing.. just blank... picture is attached..
[*]Tried killing the session, and starting new vnc sessions, but, am always met with this gray screen.
[/LIST]



**What did I miss? How do I fix this?** I have attached the gray screen. Running on ubuntu 16.04

---

### Post by TheFu on 2019-05-22
```
xsetroot -solid grey
```
That's why it is grey.

If you want a window manager or DE, then it needs to be started.  I have no idea how to start gnome. But if you have openbox, you can start it with 
```
/usr/bin/openbox &
```

If you really hate yourself, you could use twm, just remove the comment from the line.

But really, it would be a bad idea to use gnome3 inside VNC (or any remote desktop).  Gnome3 is very GPU intensive, but since you won't be using the GPU, it will be very CPU intensive.  Better to use any of the well-behaved "lite" solutions like XFCE, LXDE, Mate, ... or openbox/fluxbox/fvwm.

---

### Post by lk1234 on 2019-05-23
Thank you! Somehow this started working!

---

### Post by TheFu on 2019-05-23
> **lk1234 said:**
> Thank you! Somehow this started working!

Actually, it was working before. The script just didn't start a window manager which makes interacting with the desktop ... er ... really hard.

If this is fixed, please use the Thread Tools button at the top and mark it closed. This helps others find the solution later.

---

