---
title: "XGL, Beryl - logout and re-login does not work"
date: 2006-10-22
forum: Desktop Environments
---

### Post by Saubazi on 2006-10-22
I have Eddy with Beryl running on XGL. I have following small problem. If I logout I am not able to login in XGL again. I get something about session taking less than 10 seconds and reference to .xsession-errors. 

I have tried restarting gdm and all that but it does not help - only after reboot I get the XGL up again. 

.xsession-errors look like this:
$ more .xsession-errors 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp
 -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jykke"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Dildo:/tmp/.ICE-unix/6127
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
beryl-manager doesn't autostart window-manager/decorator
any more. Please consult: man beryl-manager


(gnome-panel:6217): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to alloc
ate widget with width -1 and height 24
evolution-alarm-notify-Message: Setting timeout for 65793 1161561600 1161495807
evolution-alarm-notify-Message:  Mon Oct 23 02:00:00 2006

evolution-alarm-notify-Message:  Sun Oct 22 07:43:27 2006

I: [dapper chroot] Running command: “firefox32 ”


I don't know is there some file or something (.lock or so) that I could delete so that relogin works? It's kind of irritating to reboot because of this and I don't understand why gdm restart does not resolve my issue...

I just tried - disabling beryl-manager and doing relogin does not help - this is purely XGL issue...

---

### Post by orb9220 on 2006-10-22
Did you post in edgy forum?
Forum : Edgy Eft (the next ubuntu release)
[http://www.ubuntuforums.org/forumdisplay.php?f=144](http://www.ubuntuforums.org/forumdisplay.php?f=144)

---

### Post by mike.thorton on 2007-01-27
same problem, after logout xgl won't work properly and accelerated desktop is out...:(

---

