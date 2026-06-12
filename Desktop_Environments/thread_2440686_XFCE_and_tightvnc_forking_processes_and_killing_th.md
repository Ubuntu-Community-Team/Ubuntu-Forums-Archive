---
title: "XFCE and tightvnc forking processes and killing the computer"
date: 2020-04-13
forum: Desktop Environments
---

### Post by csxdog on 2020-04-13
I am running Ubuntu 18.04.4 LTS.  I had tightvnc running an xfce environment.  The computer itself is running gnome.  This worked great this morning. I was able to remote in and get a fresh xfce desktop on my other computer.

Then I did something.  Not sure what. But I noticed it after I added the vncserver command to the Ubuntu startup program launcher.  It killed the system on restart.  Turned it off and figured out it happens each time I run vncserver or tightvncserver.  My .vnc directory fills up with .log and .pid files.. usually up to 25 if I manage to kill it using kill -9 `pgrep xfce`.  I figured xfce is doing something so I tried to kill it. It works most of the time.  In top, I see lots of Xtightvnc instances running.

So now, I cannot even run Tight VNC server at all.
Here's my xstartup file:
#!/bin/bash
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 > ~/ERRORS 2>&1

I added the ERRORS redirect.. here are some of the errors:

(nm-applet:2995): Gtk-WARNING **: 23:24:00.649: Can't set a parent on widget which has a parent
23:24:00.399: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:8980): Gtk-WARNING **: 23:24:00.618: Can't set a parent on widget which has a parent
:23:49.548: Can
(nm-applet:7354): Gtk-CRITICAL **: 23:24:00.398: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:7354): Gtk-CRITICAL **: 23:24:00.398: gtk_widget_destroy: assertion 'GTK_IS_WIDGET
(nm-applet:6298)
(nm-applet:7354): Gtk-WARNING **: 23:24:00.641: Can't set a parent on widget which has a parent
't set a parent on widget which has a parent
3: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

** (xfdesktop:23045): WARNING **: 23:23:52.595: Failed to set the background '/usr/share/backgrounds/xfce/xfce-teal.jpg': GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface 'org.freedesktop.DisplayManager.AccountsService'


gpg-agent: a gpg-agent is already running - not starting a new one

(xfce4-session:16133): xfce4-session-WARNING **: 23:24:07.450: gpg-agent returned no PID in the variables

(xfce4-session:16133): xfce4-session-WARNING **: 23:24:07.480: xfsm_manager_load_session: Something wrong with /home/csxdog/.cache/sessions/xfce4-session-steveslap:25, Does it exist? Permissions issue?
Xlib:  extension "RANDR" missing on display ":25.0".
Xlib:  extension "RANDR" missing on display ":25.0".


The .cache directory seems empty to me now.

BTW, when I switch my xstartup to my gnome configuration.. all is well.. and I only get about up to :3 logs and pid files (even though only :1 works).

Anyone had this issue before?

Thanks!

---

### Post by csxdog on 2020-04-14
If anyone else has this problem.. Here is the solution.. When I added this to the Gnome autostart, it uses the ~/.config/autostart directory.. which is the same used by xfce!  So even though gnome had this item disabled, xfce was just reading it and trying to start itself... over and over.  I deleted the autostart entry totally (not just disabled it), and all is well.

---

