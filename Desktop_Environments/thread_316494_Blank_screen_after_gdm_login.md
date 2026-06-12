---
title: "Blank screen after gdm login"
date: 2006-12-10
forum: Desktop Environments
---

### Post by jlintz on 2006-12-10
OK so I had aiglx and beryl working just fine.  I rebooted and bam I can't login through gdm without it just going to a blank brown screen and just a mouse cursor.  No hd activity.

I checked the logs...no errors

I can drop back to a shell and sudo startx and be in X fine without any problems so xorg.conf is fine.

I think its a program thats starting up thats causing X to hang for my session.  Anyone know what I can do about this.

---

### Post by jlintz on 2006-12-10
I forgot to mention the failsafe modes dont work either :mad:

---

### Post by ciscosurfer on 2006-12-10
Have you recently updated Beryl?  Beryl (and Compiz, for that matter) break frequently.  I'm no expert on them, but I do know this happens when their packages are updated.

I know, that probably doesn't help. :-(

---

### Post by jlintz on 2006-12-10
Nope.  This was a fresh beryl install after upgrading to edgy.  Plus beryl shouldnt be starting in failsafe mode

---

### Post by ciscosurfer on 2006-12-10
> **jlintz said:**
> Nope.  This was a fresh beryl install after upgrading to edgy.  Plus beryl shouldnt be starting in failsafe modeIt may be a fresh Beryl install, but that doesn't mean that it's not currently broken.

You're correct, Beryl shouldn't be starting in Failsafe mode, but that all depends on how you've setup Beryl to run.

---

### Post by jlintz on 2006-12-10
Do you know where X reads the startup programs for an Xsession per user?

---

### Post by ciscosurfer on 2006-12-10
> **jlintz said:**
> Do you know where X reads the startup programs for an Xsession per user?Which guide did you use to install Beryl?

---

### Post by Magni on 2007-01-15
hi
i´ve the same problem, yesterday i updated my emerald-themes package (dist-upgrade). Today i boot my Xubuntu and login with gdm, a few seconds everything was okay and then a black screen and a few seconds later i see gdm again.
i think xfce crashed when beryl is loading

i tried dpkg-reconfigure xserver-xorg


here is my /home/~/.xsession-errors:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "magni"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

(xfce4-panel:5688): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:5688): libxfcegui4-WARNING **: Disconnected from session manager.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (xffm-deskview:5721): WARNING **: cannot load /home/magni/Desktop

** (xffm-deskview:5723): WARNING **: cannot load /home/magni/Desktop

** (xffm-deskview:5727): WARNING **: cannot load /home/magni/Desktop

** (xffm-deskview:5729): WARNING **: cannot load /home/magni/Desktop

** (xffm-deskview:5725): WARNING **: cannot load /home/magni/Desktop
evolution-alarm-notify-Message: Setting timeout for 31129 1168902000 1168870871
evolution-alarm-notify-Message:  Tue Jan 16 00:00:00 2007

evolution-alarm-notify-Message:  Mon Jan 15 15:21:11 2007

X connection to :0.0 broken (explicit kill or server shutdown).

The application 'xfce4-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

(xfwm4:5682): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:5682): libxfcegui4-WARNING **: Disconnected from session manager.
ICE default IO error handler doing an exit(), pid = 5706, errno = 0
ICE default IO error handler doing an exit(), pid = 5721, errno = 2
ICE default IO error handler doing an exit(), pid = 5723, errno = 2
ICE default IO error handler doing an exit(), pid = 5725, errno = 2
ICE default IO error handler doing an exit(), pid = 5727, errno = 2
ICE default IO error handler doing an exit(), pid = 5729, errno = 2

```

have anyone an idea?

---

### Post by jlintz on 2007-01-15
I was able to fix the problem I was having by installing the ubuntu-desktop package

---

### Post by antini on 2007-01-22
I had the same problem, blank brown screen after typing my l/p. I'm not using beryl, at least to my knowledge.

Installing ubuntu-desktop fixed it for me as well.

---

### Post by Magni on 2007-01-23
install the ubuntu-desktop package??? why?
i think that's not a reason

maybe my nvidia driver  is crashed, if i run glxdemo, my desktop crash
xubuntu runs with xfwm

---

### Post by skralljt on 2008-06-03
I am having this problem intermittently.  However I have ubuntu-desktop installed also.

---

### Post by wootah on 2008-06-03
> **skralljt said:**
> I am having this problem intermittently.  However I have ubuntu-desktop installed also.
A lot has changed in a year; I would suggest that you start a new tread as this one is old.

---

