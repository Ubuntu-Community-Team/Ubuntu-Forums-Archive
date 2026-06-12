---
title: "GUI freezes during right-click Thunar operations"
date: 2011-07-06
forum: Desktop Environments
---

### Post by mister_playboy on 2011-07-06
This has been going on for a few days now... when doing anything involving an opened right-click menu in Thunar, there seems to be a chance that the entire desktop will "freeze".  I can move the mouse cursor, but cannot interact with any windows.  If I use ALT+CTR+F* to switch to a terminal session and switch back to the graphical session, all the windows on the desktop appear blank.  The computer appears to be running normally, I just can't interact with the GUI.

So far, I've just been shutting down and rebooting when this happens... any ideas on how to go about diagnosing the problem and/or regaining control of the graphical session?  I am using compositing and making non-focused windows translucent, but no other actions cause the GUI session to freeze so I don't think it's just a graphical issue.

---

### Post by Toz on 2011-07-06
Have a look at the ~/.xession-errors file (~/.xsession-errors.old if you have to reboot or relogin). Maybe a clue there that help diagnose.

---

### Post by wildmanne39 on 2011-07-06
> **mister_playboy said:**
> This has been going on for a few days now... when doing anything involving an opened right-click menu in Thunar, there seems to be a chance that the entire desktop will "freeze".  I can move the mouse cursor, but cannot interact with any windows.  If I use ALT+CTR+F* to switch to a terminal session and switch back to the graphical session, all the windows on the desktop appear blank.  The computer appears to be running normally, I just can't interact with the GUI.

So far, I've just been shutting down and rebooting when this happens... any ideas on how to go about diagnosing the problem and/or regaining control of the graphical session?  I am using compositing and making non-focused windows translucent, but no other actions cause the GUI session to freeze so I don't think it's just a graphical issue.Hi, also here is a link for freezing problems in natty.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by mister_playboy on 2011-07-07
Thanks for the help you two... my previous Ubuntu 10.10 had been my first Linux install to never freeze even once, so my troubleshooting got a little rusty over the last 8 months. :p

my .xsession-errors is mostly full of messages related to Vuze (and Vuze did have some weird graphical problems on 10.10), but the computer just froze a few minutes ago and I found these Thunar-related messages:

```
(xfce4-indicator-plugin:1461): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1461): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:1461): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:1461): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:1461): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:1461): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1461): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed

(polkit-gnome-authentication-agent-1:1478): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
(xfce4-indicator-plugin:1461): Indicator-Messages-DEBUG: new_application_item ("Pidgin Internet Messenger")
(xfce4-indicator-plugin:1461): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:1461): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:1461): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:1461): Indicator-Sound-DEBUG: new_title_widget ("gmusicbrowser")
(xfce4-indicator-plugin:1461): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(xfce4-indicator-plugin:1461): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(xfce4-indicator-plugin:1461): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
(xfce4-indicator-plugin:1461): Indicator-Application-DEBUG: Request current apps
** (nm-applet:1473): DEBUG: old state indicates that this was not a disconnect 0
(xfce4-indicator-plugin:1461): Indicator-Application-DEBUG: Building new application entry: :1.54  with icon: nm-no-connection at position 0
** (nm-applet:1473): DEBUG: foo_client_state_changed_cb
** (nm-applet:1473): DEBUG: foo_client_state_changed_cb

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 30

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 31

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 32

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 33

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 34

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 35

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 36

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 37

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 38

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 39

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 40

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 43

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 44

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 45

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 46

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 47

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 48

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 49

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 41

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 42

(xfce4-indicator-plugin:1461): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

** (xfdesktop:1437): CRITICAL **: Unable to get keyboard/mouse grab. Unable to pop up menu

** (xfdesktop:1437): CRITICAL **: Unable to get keyboard/mouse grab. Unable to pop up menu

(Thunar:1425): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
```

All prior freezes happened when copy/pasting from my internal HDD to an external one, but this freeze happened when just moving files around on the internal HDD.  I will try and gather some more info.

---

### Post by Toz on 2011-07-07
Well, here is our hint:
> ** (xfdesktop:1437): CRITICAL **: Unable to get keyboard/mouse grab. Unable to pop up menu

** (xfdesktop:1437): CRITICAL **: Unable to get keyboard/mouse grab. Unable to pop up menu

(Thunar:1425): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

Question is, what is happening an why. Can you run the following command in a terminal window and post back the results?
```
ps -ef | grep xfce4-session
```

Also, do you have nautilus installed?

---

### Post by mister_playboy on 2011-07-08
> **Toz said:**
> Question is, what is happening an why. Can you run the following command in a terminal window and post back the results?
```
ps -ef | grep xfce4-session
```

```
mister7playboy     1417  1368  0 Jul07 ?        00:00:07 xfce4-session
mister7playboy     7284  1558  0 16:01 pts/0    00:00:00 grep --color=auto xfce4-session
```

> **Toz said:**
> Also, do you have nautilus installed?

Nope! :popcorn:

---

### Post by Toz on 2011-07-09
Does anything show up in **/var/log/syslog** or **/var/log/Xorg.0.log** when the hang occurs? If not, perhaps you should create a bug report at [https://bugs.launchpad.net/ubuntu/+source/thunar]("https://bugs.launchpad.net/ubuntu/+source/thunar")

---

### Post by mister_playboy on 2011-07-10
I haven't had any freezes since my July 7th post.  Looking at /var/log/syslog, I believe this is what was recorded at the time of the freeze.

```
Jul  7 14:31:23 VGN-NR430E kernel: [75627.070179] sd 6:0:0:0: [sdc]  Sense Key : Recovered Error [current] [descriptor]
Jul  7 14:31:23 VGN-NR430E kernel: [75627.070194] Descriptor sense data with sense descriptors (in hex):
Jul  7 14:31:23 VGN-NR430E kernel: [75627.070200]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Jul  7 14:31:23 VGN-NR430E kernel: [75627.070225]         00 4f 00 c2 40 50 
Jul  7 14:31:23 VGN-NR430E kernel: [75627.070238] sd 6:0:0:0: [sdc]  ASC=0x4 ASCQ=0x1d
Jul  7 14:31:23 VGN-NR430E kernel: [75627.278446] sd 6:0:0:0: [sdc]  Sense Key : Recovered Error [current] [descriptor]
Jul  7 14:31:23 VGN-NR430E kernel: [75627.278461] Descriptor sense data with sense descriptors (in hex):
Jul  7 14:31:23 VGN-NR430E kernel: [75627.278467]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Jul  7 14:31:23 VGN-NR430E kernel: [75627.278491]         00 4f 00 c2 40 50 
Jul  7 14:31:23 VGN-NR430E kernel: [75627.278504] sd 6:0:0:0: [sdc]  ASC=0x4 ASCQ=0x1d
Jul  7 14:34:00 VGN-NR430E kernel: Kernel logging (proc) stopped.
Jul  7 14:34:00 VGN-NR430E rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="514" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul  7 14:34:41 VGN-NR430E kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jul  7 14:34:41 VGN-NR430E rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="509" x-info="http://www.rsyslog.com"] (re)start
Jul  7 14:34:41 VGN-NR430E rsyslogd: rsyslogd's groupid changed to 103
Jul  7 14:34:41 VGN-NR430E rsyslogd: rsyslogd's userid changed to 101
Jul  7 14:34:41 VGN-NR430E rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  7 14:34:41 VGN-NR430E kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  7 14:34:41 VGN-NR430E kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  7 14:34:41 VGN-NR430E kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
```

The very long series of messages at 14:34:41 looks like system bootup, and the last reboot I did was due to the freeze.

That line about "Sense Key : Recovered Error" appears in the log every 30 minutes, I don't know what it means.

/var/log/Xorg.0.log doesn't seem to show date stamps with its messages... I didn't see anything much beyond messages from every time I switched screens or plugged/unplugged my USB mouse and keyboard (since I have a laptop)

---

### Post by mister_playboy on 2011-07-17
Just to add to this... there is just one thing that triggers the freeze, making a new folder in Thunar.

So I'm just remembering to always do that from the terminal and then I have no problems. :p

---

### Post by Sangvin on 2011-10-27
Almost the same thing is happening to me on xubuntu 11.10 since the last update, the only difference is that thunar will always freeze and use 100% the cpu when i open it. Please help i really don't want to reinstall :(, here is my .xsession-errors
```

Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/adrian/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=ro_RO.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
GNOME_KEYRING_CONTROL=/tmp/keyring-aE4IDq
GNOME_KEYRING_PID=1376
GNOME_KEYRING_CONTROL=/tmp/keyring-aE4IDq
GNOME_KEYRING_CONTROL=/tmp/keyring-aE4IDq
GPG_AGENT_INFO=/tmp/keyring-aE4IDq/gpg:0:1
xfdesktop[1358]: starting up

(polkit-gnome-authentication-agent-1:1391): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
GNOME_KEYRING_CONTROL=/tmp/keyring-aE4IDq
GPG_AGENT_INFO=/tmp/keyring-aE4IDq/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-aE4IDq/ssh
** Message: applet now removed from the notification area
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher

** (process:1406): WARNING **: recent-manager-provider.vala:125: Desktop file for Aptana was not found

** (process:1406): WARNING **: recent-manager-provider.vala:125: Desktop file for exo-desktop-item-edit was not found

** (process:1406): WARNING **: recent-manager-provider.vala:125: Desktop file for exo-desktop-item-edit was not found
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

** (process:1406): WARNING **: recent-manager-provider.vala:125: Desktop file for gnome-desktop-item-edit was not found

** (process:1406): WARNING **: recent-manager-provider.vala:125: Desktop file for ristretto was not found

** (process:1406): WARNING **: recent-manager-provider.vala:125: Desktop file for gedit was not found
** (nm-applet:1414): DEBUG: foo_client_state_changed_cb

(xfdesktop:1358): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfdesktop:1358): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfdesktop:1358): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfce4-terminal:1654): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(xfdesktop:1358): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfdesktop:1358): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

```

---

### Post by Toz on 2011-10-27
@Sangvin, Can you please confirm the exact nature of your problem? Is it right-click on thunar window and thunar freezes?

Can you post back the contents of .xession-errors right after a thunar freeze (I'm not sure if the log you posted was right after a thunar freeze).

When thunar freezes, does the rest of your desktop still work?

And finally, have you tried thunar with a different login to see if its specific to your login or the whole system?

---

### Post by Sangvin on 2011-10-28
Sorry, i should have explained better. When i log into xubuntu right clicking on the desktop doesn't do anything (mouse is working i've checked and the main menu in xfce panel works) sometimes it shows the menu but with a delay of a few seconds, .xsession-errors reports ```
 ** (xfdesktop:1379): CRITICAL **: Unable to get keyboard/mouse grab. Unable to pop up menu

(xfdesktop:1379): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfdesktop:1379): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfdesktop:1379): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfdesktop:1379): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

```

Now when i open thunar it will show as usual but i cannot click anything (folder, files, even the thunar main menu does not respond) also in htop i see that thunar uses 80~100% one of my cpu cores and it will stay like this unless i kill it. I can move the thunar window around and it will draw correcly, also the min,max and close buttons work when clicked.

> When thunar freezes, does the rest of your desktop still work?
Yes everything works except the menu.

> have you tried thunar with a different login to see if its specific to your login or the whole system?
I have tried it with a new user and everything works as expected.

So what now, should i replace the .config from the new user to the old, i would really like to keep my desktop as it is though.

---

### Post by Toz on 2011-10-28
> **Sangvin said:**
> Sorry, i should have explained better. When i log into xubuntu right clicking on the desktop doesn't do anything (mouse is working i've checked and the main menu in xfce panel works)...
If right-click on the desktop isn't working, then check that **xfdesktop** is running (ps -ef | grep xfdesktop | grep -v grep). If not, then Alt+F2 and **xfdesktop --reload** to get it going again. xfdesktop controls the desktop and the menu/mouse control on the desktop. 
> ...sometimes it shows the menu but with a delay of a few seconds
This is normal, at least for me. I've never looked for a setting to remove the delay. I find that going directly to the menu on the panel is speedier
> , .xsession-errors reports ```
 ** (xfdesktop:1379): CRITICAL **: Unable to get keyboard/mouse grab. Unable to pop up menu

```
This is an interesting error message. Here is a link to a similar problem on a fedora install: [https://bugzilla.redhat.com/show_bug.cgi?id=717912]("https://bugzilla.redhat.com/show_bug.cgi?id=717912"). Whats interesting here, is that the user has a large number of images in one of the xfce-specified directories, and that is causing all the hassle. Do you have a large number of images in one of your directories? Have a look at ~/.config/user-dirs.dirs to see which directories xfce identifies as system-specific directories. If you have a large number of images in one of thos directories, try moving them elsewhere.

Also, are you cycling your background images (using "Image List" in the desktop properties)? And if so, are there a large number of images in that list?

> Now when i open thunar it will show as usual but i cannot click anything (folder, files, even the thunar main menu does not respond) also in htop i see that thunar uses 80~100% one of my cpu cores and it will stay like this unless i kill it. I can move the thunar window around and it will draw correcly, also the min,max and close buttons work when clicked.
Sure sounds like the bug mentioned above.

> I have tried it with a new user and everything works as expected.
So it is related to your profile. 

> So what now, should i replace the .config from the new user to the old, i would really like to keep my desktop as it is though.Lets try to figure out whats causing it first, before we resort to more drastic measures.

---

### Post by Sangvin on 2011-10-28
Yes, that was the problem. 
I didn't have that many images in the folder (about 28 ) but they were gigantic some were 5000x5000 or even 10000x10000 mostly all were png's and all were shown in the desktop background list. Moving them to another folder made everything work again.

Thank you very much Toz, you have saved my Xubuntu :-D

---

### Post by Toz on 2011-10-28
Glad to hear you found the problem. If you don't mind, can you mark this thread as solved using the Thread Tools link above?

You might also consider adding your name and information to the xfce bug report at: [https://bugzilla.xfce.org/show_bug.cgi?id=7834]("https://bugzilla.xfce.org/show_bug.cgi?id=7834") so that this bug can get fixed for future users.

---

### Post by Sangvin on 2011-10-29
> **Toz said:**
> Glad to hear you found the problem. If you don't mind, can you mark this thread as solved using the Thread Tools link above?

You might also consider adding your name and information to the xfce bug report at: [https://bugzilla.xfce.org/show_bug.cgi?id=7834]("https://bugzilla.xfce.org/show_bug.cgi?id=7834") so that this bug can get fixed for future users.

I added the report but i cannot mark the thread as solved since i'm not the one who started it, maybe a forum mod could do that.

---

### Post by erase on 2011-12-05
> **Sangvin said:**
> Sorry, i should have explained better. When i log into xubuntu right clicking on the desktop doesn't do anything (mouse is working i've checked and the main menu in xfce panel works) sometimes it shows the menu but with a delay of a few seconds, .xsession-errors reports

this has been bugging me for a while too. i finally got around to digging into why. if you strace the xfdesktop process, you'll notice that very soon after you right click on the desktop it starts reading in a huge number of svg icon files. if you have a drive that isn't blazingly fast or that is busy doing other things this will take a second or two.

you can disable this behavior by running xfdesktop-settings. in the Menus tab, uncheck "Show application icons in menu" or "Show applications menu on desktop right click". after you do so, things should be very quick again.

i'd argue that this should be the default for xubuntu (perhaps both off, since the application menu is accessible by default from the panel - but at least the "no icons" one)

---

### Post by mmanu on 2012-03-12
hi,
it seems i'm the new one to have this kind of (erratic) problem with thunar. i' ve a freshly installed xubuntu 11.10 with an encrypted home on a brand new 64bit CPU. my freeze is the same as the one described by the original message (by mister_playboy), although it seems that thunar try to load a huge amount of data as for sangvin (CPU at 99~101% !). here is the thing: 
the right-click menu in thunar is fine except for the "create document" submenu which doesn't popup properly (just a very small rectangle appears), the CPU races and all the desktop freezes. the mouse moves but clicking has no action, alt-ctl-F1 works, kill -9 and back to GUI brings all back to normal. .xsession-errors says : 
```
(thunar:3739): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
```  
i've tried also the "right-click on the desktop / create from template / empty file" and this one works fine (no freeze, nothing in.xsession-errors), but interestingly opening leafpad and saving the new file gives (no freeze):
```
(leafpad:3829): Gtk-WARNING **: Unable to retrieve the file info for `file:///home/mmanu/test': Error stating file '/home/mmanu/test': No such file or directory 
```
cat /var/log/syslog gives nothing after the crash
```

 Mar 12 15:12:58 nuewwa acpid: client 1150[0:0] has disconnected
 Mar 12 15:12:58 nuewwa acpid: client connected from 1150[0:0]
 Mar 12 15:12:58 nuewwa acpid: 1 client rule loaded
 Mar 12 15:12:58 nuewwa kernel: [ 3318.346431] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id 
```
as does cat /var/log/Xorg.0.log
```

 [  3205.572] (II) AIGLX: Suspending AIGLX clients for VT switch
 [  3223.211] (II) Open ACPI successful (/var/run/acpid.socket)
 [  3223.211] (II) AIGLX: Resuming AIGLX clients after VT switch
 [  3223.211] (EE) intel(0): Couldn't create pixmap for fbcon
 [  3223.327] (II) intel(0): EDID vendor "JWY", prod id 5939
 [  3223.327] (II) intel(0): Printing DDC gathered Modelines:
 [  3223.327] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
 [...]
 [  3223.327] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
```
i've reported the bug at the existing (old and closed) entry at [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/714349](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/714349)

i want to note also that the seemingly related bug (same name + "thinking a directory was a file") at [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/852410](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/852410) is affecting me too (no freeze there), although i can't reproduce it at will: the problem appeared after a logout/login with either the folder of my external HD, which became an unopenable file in thunar (with its path as a name) or with the "network" entry in the shortcut side pane. this weird behavior of thunar was one of the reason of my downgrade to 11.10, when i tried the 12.04 alpha a couple of days ago (with some problem to create/access to an external HD encrypted partition, which are by the way ok with 11.10). i'm very disappointed to find it back here!

for information, i've changed the places' names in .config/user-dirs.dirs, i've all my files in these folders (50G) and no image list for my background...

---

### Post by mmanu on 2012-03-13
i checked on my asus T91MT xubuntu lucid LTS (not encrypted, modified user-dirs.dirs) and the same .xsession-error occurs
```
(thunar:1343): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed 
```
when opening the "Create Document" submenu, but without the freeze.

i redid (see previous post) the leafpad test also with my lucid eeepc (open mousepad & create/save an empty file) but there no errors message in xsession-errors.

---

### Post by mmanu on 2012-03-13
i tried it on the guest account and here is the result:
no freeze, but the same .xsession-error just after the right-click.
the "create document" submenu is fine and the error appears not to be related to its opening but just to the right-click menu opening.
i retried with my session & indeed, the right-click suffices to procude the error and the freeze doesn't occur. then i place my mouse on "create document", the GUI freezes without additional error message

---

### Post by mmanu on 2012-03-13
OK, i've got it!!!!
all was the fault of the XDG_TEMPLATES_DIR, that i used to put some of my unclassified pdf, without knowing what's the purpose of that directory : create a list of templates used to create documents ... accessible by right clicking in thunar under the "create document" entry !!! obvious!

the only reason i used all the predefined folders of user-dirs.dirs is that they have emblems as folder-icons in thunar side pane and in thunar compact list (with very small size) and it looks nice. someone knows how to define the icon of a given folder as it's done for the predefined XDG_DIRS ?

---

### Post by daniroma on 2013-01-29
Yes, same problem, same solution.

I removed all files from Templates ( filled with icons and linux program files that I use  - moved to other folder).

Thunar is reliable again!

---

### Post by den-el-vegano on 2013-10-12
I had a similar problem in Xubuntu 12.04 : Thunar would freeze every time i would launch it - but gksudo thunar would work without a problem.

My solution was removing everything that was in the Templates folder in my home folder.

Thanks! This made my day!

---

