---
title: "VNC: Could not acquire name on session bus"
date: 2010-05-11
forum: Desktop Environments
---

### Post by boss451 on 2010-05-11
Hi, everyone.

I had just updated from 9.10 to 10.04. After update my vncserver doesn't work properly.

I can start server, but when I'm connecting to it I obtain grey screen with window which tells me: Could not acquire name on session bus.

If I run vncserver under root,```
sudo vncserver
``` it works fine. Before update it worked well, too.

In .xsession-errors I have this:
> 
Xsession: X session started for ashkop at Tue May 11 16:39:36 EEST 2010
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Setting IM through im-switch for locale=ru_UA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** Message: Another GPG agent already running

x-session-manager[3282]: WARNING: Failed to acquire org.gnome.SessionManager


Can you help me?

---

### Post by boss451 on 2010-05-19
Solved it.

Add 
```
unset DBUS_SESSION_BUS_ADDRESS
```
to ~/.vnc/xstartup file after
```
unset SESSION_MANAGER
```

---

### Post by dennislindsey on 2010-08-10
I updated Ubuntu 10.04, rebooted, and vncserver came up with a grey background without the Gnome session.  A dialog box read "Could not acquire name on session bus".

FOUND MY SOLUTION:

[FONT=System]   sudo chmod 755 /etc/X11/xinit/xinitrc[/FONT]

The ~/.vnc/xstartup now starts Gnome and panels as expected, it reads:

[FONT=Courier New]#!/bin/sh
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# [ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
# [ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
# vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
exec /etc/X11/xinit/xinitrc
# x-window-manager &
# gnome-session &[/FONT]

---

### Post by richgreene on 2012-03-30
Adding the line:  

[FONT="Courier New"][INDENT][/INDENT]unset DBUS_SESSION_BUS_ADDRESS
[/FONT]
fixed all my problems with VNC.  I'm using Ubuntu 11.1 and here is my latest xstartup for reference:
[FONT="Courier New"]
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
#. /etc/X11/xinit/xinitrc
/usr/bin/gnome-session --session=gnome-classic

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
[/FONT]

---

