---
title: "Beryl Install: Couldn't exec startxgl"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by D2Hitman on 2007-04-04
Trying to install Beryl from the guide [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html). I get through the entire guide, but when i try to run Beryl, I get to the select session on the ubuntu login screen, run XGL part and i get an error saying my session has lasted less than 10 seconds and failed. 

Under view details (~/.xsessions-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x /var/lib/gdm/:0.Xservers" -h "" -l ":0" "usrname"

/etc/gdm/Xsession: Beginning session startup...

Couldn't exec /usr/bin/startxgl: No such file of directory

and from this point on i only have access to the failsafe terminal. Any ideas would be much appreciated! Thanks.

P.S. there is definitely a file named /usr/bin/startxgl and it is executable!

---

### Post by geirha on 2007-04-04
Well, there must be a reason why it can't find it, so just to make sure; you named the startxgl script with only lowercase letters? And it has execute permissions for your user (not just root)?
```
ls -l /usr/bin/start*
``` from a terminal-window should be helpful.

---

### Post by D2Hitman on 2007-04-04
ls -l /usr/bin/start* returns

> -rwxr-xr-x 1 root root 5712 2007-03-29 00:25 /usr/bin/start_kdeinit
-rwxr-xr-x 1 root root 3838 2006-08-07 20:01 /usr/bin/startx
-rwxr-xr-x 1 root root  134 2007-04-04 17:43 /usr/bin/startxgl

/usr/share/xsessions/xgl.desktop contains

> [Desktop Entry]
Encoding=UTF-8
Name=XGL
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl
Icon=
Type=Application

am i missing something?

---

### Post by geirha on 2007-04-04
That looks correct, and should work. Only other thing I can think of is that there's a typo or something in the script itself, what does the content of /usr/bin/startxgl look like?

The first line would be the most likely place. Try changing it to: ```
#!/bin/bash
```

---

### Post by D2Hitman on 2007-04-04
The file /usr/bin/startxgl
> #!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

changing sh to bash doesnt help the problem. However i have fixed the problem for the moment by stopping beryl-manager from loading on startup, but this doesnt really explain the error message. Thanks for the help and any real fixes you could think of!

---

### Post by geirha on 2007-04-04
hm... ok. I would expect a different error message really, but maybe one of the three programs started from this script isn't there? you can check using **which**:
```
$ which Xgl dbus-launch gnome-session
/usr/bin/Xgl
/usr/bin/dbus-launch
/usr/bin/gnome-session
```
If you lack one of them, these are the packages they are installed with:
```
$ which Xgl dbus-launch gnome-session | xargs dpkg -S | cut -d: -f1
xserver-xgl
dbus
gnome-session
```
I just can't see any other reason for the script to fail... I'm out of ideas beyond this :(

---

### Post by D2Hitman on 2007-04-07
All of those 3 are there. Manually starting beryl-manager doesn't seem to have any problems, just an inconvenience. Thanks for the help.

---

