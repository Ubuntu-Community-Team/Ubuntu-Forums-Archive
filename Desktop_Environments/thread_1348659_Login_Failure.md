---
title: "Login Failure"
date: 2009-12-07
forum: Desktop Environments
---

### Post by richard.e.morton on 2009-12-07
I have installed a Xubuntu 9.10 onto a usb stick (twice, two different sticks). I have also installed Kubuntu and Ubuntu and this problem is not present.

I noticed that on login into Xubuntu there are three possible sessions I can start,
two called XFCE session and one XTERM session... I find there being 2
different XFCE sessions as being a little strange. This is as it is
out of the box installed from the released iso of 9.10.

The system is set to autologin with Myth. And this works fine, logging
in perfectly.

All works fine for a while with Myth 0.21. Then Myth crashes and takes
the system with it, ALT+F2 does nothing, ssh server doesn't respond...
I haven't been able to work out why.

After this episode, a start (or restart) is a hit or miss affair with
it sometimes logging in and sometimes it goes momentarily to a white
screen and coming to the login screen, logging in often starts the
login process and then comes to the white screen, trying the two
different XCFE sessions listed sometimes gets it to login, mostly not,
being persistent (sometimes with a reboot) always gets a login -
eventually... greeter log contains:

root@myth-bedroom:/var/log/gdm# cat :0-greeter.log.1
gnome-session[1579]: devkit-power-gobject-WARNING: Couldn't enumerate
devices: The name org.freedesktop.DeviceKit.Power was not provided by
any .service files
gnome-session[1579]: WARNING: Could not launch application
'metacity.desktop': Unable to start application: Failed to execute
child process "metacity" (No such file or directory)
gnome-session[1579]: WARNING: Could not launch application
'gnome-power-manager.desktop': Unable to start application: Failed to
execute child process "gnome-power-manager" (No such file or
directory)
** (process:1591): DEBUG: Greeter session pid=1591 display=:0.0
xauthority=/var/run/gdm/auth-for-gdm-aWeoqd/database
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Couldn't
enumerate devices: The name org.freedesktop.DeviceKit.Power was not
provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Error invoking
GetAll() to get properties: The name org.freedesktop.DeviceKit.Power
was not provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Error invoking
GetAll() to get properties: The name org.freedesktop.DeviceKit.Power
was not provided by any .service files
gdm-simple-greeter[1591]: GVFS-RemoteVolumeMonitor-WARNING: cannot
open directory /usr/share/gvfs/remote-volume-monitors: Error opening
directory '/usr/share/gvfs/remote-volume-monitors': No such file or
directory
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Couldn't
enumerate devices: The name org.freedesktop.DeviceKit.Power was not
provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Error invoking
GetAll() to get properties: The name org.freedesktop.DeviceKit.Power
was not provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Couldn't
enumerate devices: The name org.freedesktop.DeviceKit.Power was not
provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Error invoking
GetAll() to get properties: The name org.freedesktop.DeviceKit.Power
was not provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Couldn't
enumerate devices: The name org.freedesktop.DeviceKit.Power was not
provided by any .service files
gdm-simple-greeter[1591]: devkit-power-gobject-WARNING: Error invoking
GetAll() to get properties: The name org.freedesktop.DeviceKit.Power
was not provided by any .service files

(xfwm4:1592): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:1592): libxfcegui4-WARNING **: Disconnected from session manager.


mythfrontend.log is full of
X Error: BadRequest (invalid request code or no such operation) 1
 Major opcode:  132
 Minor opcode:  18
 Resource id:  0x2a0001b
X Error: BadRequest (invalid request code or no such operation) 1
 Major opcode:  132
 Minor opcode:  18
 Resource id:  0x2a0001b
X Error: BadRequest (invalid request code or no such operation) 1
 Major opcode:  132
 Minor opcode:  18
 Resource id:  0x2a0001b
X Error: BadRequest (invalid request code or no such operation) 1
 Major opcode:  132
 Minor opcode:  18
 Resource id:  0x2a0001b
X Error: BadRequest (invalid request code or no such operation) 1
 Major opcode:  132^C


I am still looking to catch the error in the log as the log file was 500MB...

Any ideas where else I should look and what other info I should grab
to debug this?

---

### Post by ashishb on 2010-01-31
were you able to find a solution to that?
I am facing the same problem
[while running the system, X crashed suddenly, now I can login with other accounts but not with the original one] and getting the same error message.

---

### Post by ashishb on 2010-01-31
I am having the same error and able to resolve it.
You need to delete ~/.ICEauthority file.

---

### Post by jonnybignote on 2010-07-21
sorry to hijack...

don't know if I have a different problem but that works for me once and then the following reboot, the problem is there again...does that sound familiar to anyone?
Thanks

---

### Post by Darkmoon_UK on 2010-09-25
Quite an alarming problem when you can't log in! Thanks ashishb - your solution fixed this for me. :)

---

