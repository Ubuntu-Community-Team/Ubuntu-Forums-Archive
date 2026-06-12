---
title: "There was an error starting the GNOME Settings Daemon."
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by sp0ki on 2007-09-15
Hi, I have a problem.. when I start my Ubuntu I have to wait more than 5 minutes to log on and then there is this massage telling me that something is wrong with the GNOME Settings Daemon. Please, if somebody can help me, I'll be glad. This is the massage:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by admbe on 2007-09-18
Same issue here. I also noticed that my loop back adapter does not start.. I have to do sudo ifconfig lo up before starting services such as mysql and azerues. I wonder if gnome-settings somehow needs this....

TIA

---

### Post by rare HERO on 2008-02-13
I have the same error:

There was an error starting the GNOME Settings Daemon.

[PHP]Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/PHP]

I looked up my ~/.xsession-errors file and it says:
[PHP](process:6231): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6235): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/rare-desktop:/tmp/.ICE-unix/6228
Window manager warning: Failed to read saved session file /home/rare/.metacity/sessions/default0.ms: Failed to open file '/home/rare/.metacity/sessions/default0.ms': No such file or directory
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
** Message: Not starting remote desktop server
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused
evolution-alarm-notify-Message: Setting timeout for 1841 1202886000 1202884159
evolution-alarm-notify-Message:  Wed Feb 13 00:00:00 2008

evolution-alarm-notify-Message:  Tue Feb 12 23:29:19 2008

libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused

(gnome-panel:6290): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x80f6958

(gnome-panel:6290): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x80f6958
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused
system-config-printer-applet: unable to initialize pynotify
system-config-printer-applet: failed to connect to session D-Bus
ERROR: tracker_dbus_init() could not get the session bus
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Wed Feb 13 00:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rare/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rare/.evolution/calendar/local/system - Calendar Open Async... 0x80a5a70
alarm-notify.c:220 (load_calendars) - Loading Calendar webcal://sports.yahoo.com/ncaaw/teams/aar/ical.ics 
alarm-notify.c:462 (alarm_notify_add_calendar) webcal://sports.yahoo.com/ncaaw/teams/aar/ical.ics - Calendar Open Async... 0x80b5430
alarm-notify.c:220 (load_calendars) - Loading Calendar webcal://sports.yahoo.com/ncaab/teams/aar/ical.ics 
alarm-notify.c:462 (alarm_notify_add_calendar) webcal://sports.yahoo.com/ncaab/teams/aar/ical.ics - Calendar Open Async... 0x80b5580
alarDBUS ERROR: org.freedesktop.DBus.Error.NoServer occurred with message Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused
process 6320: arguments to dbus_connection_register_object_path() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5280.
This is normally a bug in some application using the D-Bus library.
m-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80c1920
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rare/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rare/.evolution/tasks/local/system - Calendar Open Async... 0x80c1b60
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rare/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rare/.evolution/memos/local/system - Calendar Open Async... 0x80c5330
alarm-notify.c:393 (cal_opened_cb) file:///home/rare/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/rare/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) webcal://sports.yahoo.com/ncaab/teams/aar/ical.ics - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80c6600: Received at thread b5dc1b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c1b60
alarm-queue.c:581 (load_alarms_for_today) - From Tue Feb 12 23:29:24 2008
 to Tue Feb 12 23:29:24 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80c6600: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x80c4cc0: Received at thread b5dc1b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80a5a70
alarm-queue.c:581 (load_alarms_for_today) - From Tue Feb 12 23:29:24 2008
 to Tue Feb 12 23:29:24 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80c4cc0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x80b5bc8: Received at thread b5dc1b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80b5580
alarm-queue.c:581 (load_alarms_for_today) - From Tue Feb 12 23:29:24 2008
 to Tue Feb 12 23:29:24 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80b5bc8: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80c6cf8: Received at thread b5dc1b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c1920
alarm-queue.c:581 (load_alarms_for_today) - From Tue Feb 12 23:29:25 2008
 to Tue Feb 12 23:29:25 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80c6cf8: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) webcal://sports.yahoo.com/ncaaw/teams/aar/ical.ics - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_Initializing gnome-mount extension
  PID TTY          TIME CMD

** (update-notifier:6311): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (update-notifier:6311): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (update-notifier:6311): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
Traceback (most recent call last):
  File "/usr/bin/deluge", line 132, in <module>
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 218, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 107, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
checking for valid crashreport now
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.

** (update-notifier:6311): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed[/PHP]

Anything???

---

