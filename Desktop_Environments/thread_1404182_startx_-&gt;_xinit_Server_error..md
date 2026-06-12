---
title: "startx -&gt; xinit: Server error."
date: 2010-02-11
forum: Desktop Environments
---

### Post by shabs on 2010-02-11
Hi!
I've been running 8.10 on a desktop for a month now. Its been working fine. I've been using it for some project work.
I had to reboot the computer (I used to have it on all the time) and when it rebooted it takes me to the CLI and there is no GUI.
When I "startx" at the terminal I get an error that says "xinit: Server error"

Here are the things I've already tried:
1. sudo dpkg-reconfigure xserver-xorg
This skips the steps for the graphics card, does the keyboard configuration and then ends without the mouse and monitor configuration.

2. sudo apt-get install --reinstall gdm
Gets stuck at 'setting up ssl-cert (1.0.23)

3. sudo aptitude install ubuntu-desktop (I guess same command as above)
Gets stuck at 'setting up ssl-cert (1.0.23) again.

It was working fine so I don't know if its really a problem with my video driver.

Anybody has any other ideas? Any help would be appreciated as I'm stuck with this and this computer has a lot of information and configuration that I've been working on lately and don't wish to reinstall.

Warm wishes,
Shabs.

---

### Post by flippo on 2010-02-11
Can you take a look at / post your .xsession-errors (~/.xsession-errors)?  Also, is GDM installed, can you do sudo /etc/init.d/gdm start?

---

### Post by shabs on 2010-02-11
Hi!
Thanks for your reply.
sudo /etc/init.d/gdb start results in a 

"* Strating GNOME Display Manager...                                                     [OK]"

but thats it and nothing comes up.

The file is below:

```
/etc/gdm/Xsession: Beginning session setup...
/home/y/.profile: 26: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/ssl/bin:/usr/local/ssl/bin: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[4833]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
x-session-manager[4833]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Initializing nautilus-share extension

** (nautilus:5070): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

x-session-manager[4833]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout

** (nm-applet:5110): WARNING **: No connections defined


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Failure: Module initalization failed
starting HAL detection for ac adaptors...none found
evolution-alarm-notify-Message: Setting timeout for 44185 1262304000 1262259815
evolution-alarm-notify-Message:  Fri Jan  1 01:00:00 2010

evolution-alarm-notify-Message:  Thu Dec 31 12:43:35 2009

Throttle level is 0

(nm-connection-editor:5164): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed
** Message: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /etc/NetworkManager/VPN.

** (nm-connection-editor:5164): WARNING **: No connections defined

(nm-connection-editor:5164): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262304000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262390400 1262304000
evolution-alarm-notify-Message:  Sat Jan  2 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan  1 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1262390400 1262304000
evolution-alarm-notify-Message:  Sat Jan  2 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan  1 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262390400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262476800 1262390400
evolution-alarm-notify-Message:  Sun Jan  3 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan  2 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1262476800 1262390400
evolution-alarm-notify-Message:  Sun Jan  3 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan  2 01:00:00 2010

alarm-notify.c:240 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1851 (alarm_queue_init)
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Fri Jan  1 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Jan  2 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sun Jan  3 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262476800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262563200 1262476800
evolution-alarm-notify-Message:  Mon Jan  4 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan  3 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1262563200 1262476800
evolution-alarm-notify-Message:  Mon Jan  4 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan  3 01:00:00 2010

** Message: don't know how to handle video/x-divx, divxversion=(int)5, framerate=(fraction)25/1, width=(int)560, height=(int)240
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, codec_data=(buffer)010002000000800101000000
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2307): prepare_output (): /GstPlayBin:play

** Message: don't know how to handle video/x-divx, divxversion=(int)5, framerate=(fraction)25/1, width=(int)560, height=(int)240
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, codec_data=(buffer)010002000000800101000000
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2307): prepare_output (): /GstPlayBin:play

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262563200
night_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Mon Jan  4 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarmevolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262649600 1262563200
evolution-alarm-notify-Message:  Tue Jan  5 01:00:00 2010

evolution-alarm-notify-Message:  Mon Jan  4 01:00:00 2010


(gnome-terminal:5231): Vte-WARNING **: No handler for control sequence `ansi-conformance-level-3' defined.
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262649600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262736000 1262649600
evolution-alarm-notify-Message:  Wed Jan  6 01:00:00 2010

evolution-alarm-notify-Message:  Tue Jan  5 01:00:00 2010

-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Tue Jan  5 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Wed Jan  6 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262736000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262822400 1262736000
evolution-alarm-notify-Message:  Thu Jan  7 01:00:00 2010

evolution-alarm-notify-Message:  Wed Jan  6 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262822400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1262908800 1262822401
evolution-alarm-notify-Message:  Fri Jan  8 01:00:00 2010

evolution-alarm-notify-Message:  Thu Jan  7 01:00:01 2010

h)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Thu Jan  7 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Fri Jan  8 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnighevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262908800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1262995200 1262908800
evolution-alarm-notify-Message:  Sat Jan  9 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan  8 01:00:00 2010

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1262995200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263081600 1262995200
evolution-alarm-notify-Message:  Sun Jan 10 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan  9 01:00:00 2010

t_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Jan  9 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sun Jan 10 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (checkevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263081600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1263168000 1263081601
evolution-alarm-notify-Message:  Mon Jan 11 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan 10 01:00:01 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263168000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Mon Jan 11 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at evolution-alarm-notify-Message: Setting timeout for 86400 1263254400 1263168000
evolution-alarm-notify-Message:  Tue Jan 12 01:00:00 2010

evolution-alarm-notify-Message:  Mon Jan 11 01:00:00 2010


** (gnome-system-monitor:29175): WARNING **: SELinux was found but is not enabled.


** (gnome-system-monitor:29191): WARNING **: SELinux was found but is not enabled.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263254400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263340800 1263254400
evolution-alarm-notify-Message:  Wed Jan 13 01:00:00 2010

evolution-alarm-notify-Message:  Tue Jan 12 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1263340800 1263254400
evolution-alarm-notify-Message:  Wed Jan 13 01:00:00 2010

evolution-alarm-notify-Message:  Tue Jan 12 01:00:00 2010

Tue Jan 12 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Wed Jan 13 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_reevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263340800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263427200 1263340800
evolution-alarm-notify-Message:  Thu Jan 14 01:00:00 2010

evolution-alarm-notify-Message:  Wed Jan 13 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263427200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1263513600 1263427201
evolution-alarm-notify-Message:  Fri Jan 15 01:00:00 2010

evolution-alarm-notify-Message:  Thu Jan 14 01:00:01 2010

fresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Thu Jan 14 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Fri Jan 15 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263513600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263600000 1263513600
evolution-alarm-notify-Message:  Sat Jan 16 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan 15 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263600000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263686400 1263600000
evolution-alarm-notify-Message:  Sun Jan 17 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan 16 01:00:00 2010

night_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Jan 16 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sun Jan 17 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (cevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263686400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263772800 1263686400
evolution-alarm-notify-Message:  Mon Jan 18 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan 17 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263772800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1263859200 1263772801
evolution-alarm-notify-Message:  Tue Jan 19 01:00:00 2010

evolution-alarm-notify-Message:  Mon Jan 18 01:00:01 2010

heck_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Mon Jan 18 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Tue Jan 19 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c
(firefox:29181): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:29181): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:29181): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:29181): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:29181): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:29181): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:29181): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:29181): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:29181): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:29181): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:29181): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:29181): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263859200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1263945600 1263859200
evolution-alarm-notify-Message:  Wed Jan 20 01:00:00 2010

evolution-alarm-notify-Message:  Tue Jan 19 01:00:00 2010

:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Wed Jan 20 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnighevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1263945600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264032000 1263945600
evolution-alarm-notify-Message:  Thu Jan 21 01:00:00 2010

evolution-alarm-notify-Message:  Wed Jan 20 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264032000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1264118400 1264032001
evolution-alarm-notify-Message:  Fri Jan 22 01:00:00 2010

evolution-alarm-notify-Message:  Thu Jan 21 01:00:01 2010

t_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Thu Jan 21 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Fri Jan 22 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (checkevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264118400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264204800 1264118400
evolution-alarm-notify-Message:  Sat Jan 23 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan 22 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264204800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264291200 1264204800
evolution-alarm-notify-Message:  Sun Jan 24 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan 23 01:00:00 2010

_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Jan 23 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sun Jan 24 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:182evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264291200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1264377600 1264291201
evolution-alarm-notify-Message:  Mon Jan 25 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan 24 01:00:01 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264377600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264464000 1264377600
evolution-alarm-notify-Message:  Tue Jan 26 01:00:00 2010

evolution-alarm-notify-Message:  Mon Jan 25 01:00:00 2010

1 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Mon Jan 25 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Tue Jan 26 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264464000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264550400 1264464000
evolution-alarm-notify-Message:  Wed Jan 27 01:00:00 2010

evolution-alarm-notify-Message:  Tue Jan 26 01:00:00 2010

ue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Wed Jan 27 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264550400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264636800 1264550400
evolution-alarm-notify-Message:  Thu Jan 28 01:00:00 2010

evolution-alarm-notify-Message:  Wed Jan 27 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264636800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264723200 1264636800
evolution-alarm-notify-Message:  Fri Jan 29 01:00:00 2010

evolution-alarm-notify-Message:  Thu Jan 28 01:00:00 2010

night_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Thu Jan 28 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Fri Jan 29 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (cevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264723200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264809600 1264723200
evolution-alarm-notify-Message:  Sat Jan 30 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan 29 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1264809600 1264723200
evolution-alarm-notify-Message:  Sat Jan 30 01:00:00 2010

evolution-alarm-notify-Message:  Fri Jan 29 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264809600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264896000 1264809600
evolution-alarm-notify-Message:  Sun Jan 31 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan 30 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1264896000 1264809600
evolution-alarm-notify-Message:  Sun Jan 31 01:00:00 2010

evolution-alarm-notify-Message:  Sat Jan 30 01:00:00 2010

heck_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Jan 30 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sun Jan 31 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.cevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264896000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1264982400 1264896000
evolution-alarm-notify-Message:  Mon Feb  1 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan 31 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1264982400 1264896000
evolution-alarm-notify-Message:  Mon Feb  1 01:00:00 2010

evolution-alarm-notify-Message:  Sun Jan 31 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1264982400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1265068800 1264982400
evolution-alarm-notify-Message:  Tue Feb  2 01:00:00 2010

evolution-alarm-notify-Message:  Mon Feb  1 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1265068800 1264982400
evolution-alarm-notify-Message:  Tue Feb  2 01:00:00 2010

evolution-alarm-notify-Message:  Mon Feb  1 01:00:00 2010

:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Mon Feb  1 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Tue Feb  2 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarmevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265068800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1265155200 1265068801
evolution-alarm-notify-Message:  Wed Feb  3 01:00:00 2010

evolution-alarm-notify-Message:  Tue Feb  2 01:00:01 2010

evolution-alarm-notify-Message: Setting timeout for 86399 1265155200 1265068801
evolution-alarm-notify-Message:  Wed Feb  3 01:00:00 2010

evolution-alarm-notify-Message:  Tue Feb  2 01:00:01 2010

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265155200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Wed Feb  3 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_reevolution-alarm-notify-Message: Setting timeout for 86400 1265241600 1265155200
evolution-alarm-notify-Message:  Thu Feb  4 01:00:00 2010

evolution-alarm-notify-Message:  Wed Feb  3 01:00:00 2010

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265241600
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1265328000 1265241600
evolution-alarm-notify-Message:  Fri Feb  5 01:00:00 2010

evolution-alarm-notify-Message:  Thu Feb  4 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1265328000 1265241600
evolution-alarm-notify-Message:  Fri Feb  5 01:00:00 2010

evolution-alarm-notify-Message:  Thu Feb  4 01:00:00 2010


(gnome-terminal:5231): Vte-WARNING **: No handler for control sequence `ansi-conformance-level-3' defined.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

fresh) - Refresh at Thu Feb  4 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Fri Feb  5 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:182evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265328000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1265414400 1265328000
evolution-alarm-notify-Message:  Sat Feb  6 01:00:00 2010

evolution-alarm-notify-Message:  Fri Feb  5 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1265414400 1265328000
evolution-alarm-notify-Message:  Sat Feb  6 01:00:00 2010

evolution-alarm-notify-Message:  Fri Feb  5 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265414400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1265500800 1265414400
evolution-alarm-notify-Message:  Sun Feb  7 01:00:00 2010

evolution-alarm-notify-Message:  Sat Feb  6 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1265500800 1265414400
evolution-alarm-notify-Message:  Sun Feb  7 01:00:00 2010

evolution-alarm-notify-Message:  Sat Feb  6 01:00:00 2010

1 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Feb  6 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sun Feb  7 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queevolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265500800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1265587200 1265500800
evolution-alarm-notify-Message:  Mon Feb  8 01:00:00 2010

evolution-alarm-notify-Message:  Sun Feb  7 01:00:00 2010

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1265587200
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1265673600 1265587200
evolution-alarm-notify-Message:  Tue Feb  9 01:00:00 2010

evolution-alarm-notify-Message:  Mon Feb  8 01:00:00 2010

evolution-alarm-notify-Message: Setting timeout for 86400 1265673600 1265587200
evolution-alarm-notify-Message:  Tue Feb  9 01:00:00 2010

evolution-alarm-notify-Message:  Mon Feb  8 01:00:00 2010

ue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Mon Feb  8 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Tue Feb  9 01:00:00 2010
 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
a
(gnome-keyring-daemon-wrapper:4974): EggSMClient-WARNING **: Received XSMP SaveYourself message in state save-yourself-done: client or server error
```

Thanks :)

---

### Post by shabs on 2010-02-11
Also the reason that my efforts at updating get stuck at 'setting up ssl-cert' is probably because I've been playing around with openssl on the computer. I've removed the default and installed an older version of openssl.

Shabs.

---

### Post by flippo on 2010-02-11
Can you also give:
```
sudo cat /var/log/Xorg.0.log | grep \(WW\)
and
sudo cat /var/log/Xorg.0.log | grep \(EE\)
```

I would also try removing and reinstalling ssl-cert.

---

### Post by shabs on 2010-02-11
Hi,
Here they are:
```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000207 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Failed to allocate texture space.
```

and 

	```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
(EE) intel(0): underrun on pipe A!
```

I'm afraid of reinstalling ssl-cert as I think it might also update the openssl package to the latest one in the repos.
What do you think?

Shabs.

---

