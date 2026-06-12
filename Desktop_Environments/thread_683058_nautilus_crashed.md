---
title: "nautilus crashed"
date: 2008-01-30
forum: Desktop Environments
---

### Post by hollowhead on 2008-01-30
Nautilus brought my machine low and I had to back out using ctrl-alt backspace, ny wallpaper dissapeared when logging in and no nautilus dependent apps worked.  Logging back in was a waste of time although logging in as my wife worked fine.  I had to reboot the machine.  My nautilus debug file 

===== BEGIN MILESTONES =====
0x8177880 2008/01/30 20:16:33.9202 (GLog): failed to load session from /home/nrh1/.nautilus/saved-session-EDPE3T
0x8177880 2008/01/30 20:20:27.7441 (GLog): Cannot extract frame (0, 0) from the grid

0x8177880 2008/01/30 20:25:39.7895 (GLog): Cannot extract frame (0, 0) from the grid

0x8177880 2008/01/30 20:26:05.8625 (USER): debug log dumped due to signal 11
0x8177880 2008/01/30 20:26:05.8642 (USER): debug log dumped due to signal 11
0x8177880 2008/01/30 20:26:05.8644 (USER): debug log dumped due to signal 11

and xsession-error files are shown below


(process:5945): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5949): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/hollowfamily:/tmp/.ICE-unix/5942
** Message: Not starting remote desktop server


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
xscreensaver: unknown option "&".  Try "-help".
evolution-alarm-notify-Message: Setting timeout for 11205 1201737600 1201726395
evolution-alarm-notify-Message:  Thu Jan 31 00:00:00 2008

evolution-alarm-notify-Message:  Wed Jan 30 20:53:15 2008

evolution-alarm-notify-Message: Setting timeout for 11205 1201737600 1201726395
evolution-alarm-notify-Message:  Thu Jan 31 00:00:00 2008

evolution-alarm-notify-Message:  Wed Jan 30 20:53:15 2008

Throttle level is 0
Initializing gnome-mount extension
** Message: failed to load session from /home/nrh1/.nautilus/saved-session-EDPE3T

(evolution-alarm-notify:6018): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Thu Jan 31 00:00:00 2008
 
  PID TTY          TIME CMD
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3600058 specified for 0x3600127 (acroread).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3600058 specified for 0x3600295 (Adobe Read).
fetchDevices
Lock acquired for devices thread
Devices thread started
Connecting (devices)
Fetching devices
Closing connection (devices)
Releasing devices lock
Got devices
queryPPDs
Lock acquired for PPDs thread
PPDs thread started
Connecting (PPDs)
Fetching PPDs
fetchPPDs
queryPPDs
queryPPDs: in progress
Closing connection (PPDs)
Releasing PPDs lock
Got PPDs
set PageSize = A4
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3000d3b (OpenOffice)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3000d3b (OpenOffice)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (nautilus:5997): WARNING **: Cannot extract frame (0, 0) from the grid


** (gedit:6614): WARNING **: Cannot extract frame (0, 0) from the grid


** (nautilus:5997): WARNING **: Cannot extract frame (0, 0) from the grid


Immediately before I had been running smartctl on my harddrive but had logged out and logged back in and immediately after lost all the toolbar and other icons in all oo apps I installed the tango icons and this restored oo.  There is no crash registered in var/crash.

Sorry about the length of post but is there any way of stopping this happening again?  I have had to reinstall once due to nautilus corruption already.  gnome is very dependent on this app.   smartctl short test indicated that hard disk was ok.

---

### Post by miatawnt2b on 2008-02-11
Same issue here.  Did you find a fix?
-J

---

