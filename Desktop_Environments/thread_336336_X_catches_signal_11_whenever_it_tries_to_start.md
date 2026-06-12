---
title: "X catches signal 11 whenever it tries to start"
date: 2007-01-11
forum: Desktop Environments
---

### Post by tarkus on 2007-01-11
I have an existing working setup on Edgy.  I didn't install any updates - last night I shut it off fine and this morning I get 
> steven@platypus:~$ tail -f /var/log/Xorg.0.log
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Thu Jan 11 10:41:37 2007: 7093 X: client 2 rejected from local host
AUDIT: Thu Jan 11 10:41:37 2007: 7093 X: client 4 rejected from local host
AUDIT: Thu Jan 11 10:41:37 2007: 7093 X: client 3 rejected from local host
AUDIT: Thu Jan 11 10:41:37 2007: 7093 X: client 6 rejected from local host
AUDIT: Thu Jan 11 10:41:37 2007: 7093 X: client 5 rejected from local host

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting
every time I try to start X.  This happens whether it's started from gdm or startx.  I have made no configuration changes from my last working one...  Any ideas?

Thanks,
Steven

---

### Post by tarkus on 2007-01-11
Oh, and for the record the "Failsafe XTerm" session choice works fine.

---

### Post by tarkus on 2007-01-11
.xsession-errors is:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "steven"
synergyc: no process killed
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/platypus:/tmp/.ICE-unix/6306
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

(evolution-alarm-notify:6406): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
X connection to :0.0 broken (explicit kill or server shutdown).
evolution-alarm-notify-Message: Setting timeout for 80268 1168646400 1168566132
evolution-alarm-notify-Message:  Fri Jan 12 16:00:00 2007

evolution-alarm-notify-Message:  Thu Jan 11 17:42:12 2007

libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-EsE08YlhPm: Connection refused
although it doesn't seem to have anything interesting...

---

### Post by maja.m on 2007-04-09
If you are using beryl you have better to disable it. I had the same problem after a power fail... 
Is there anyone who knows how to make beryl work again in such a situation?

---

### Post by maja.m on 2007-04-09
Ok, I found a solution for me.
I recompiled the nvidia drivers and now I can use beryl too.

---

