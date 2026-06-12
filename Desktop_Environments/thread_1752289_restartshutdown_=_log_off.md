---
title: "restart/shutdown = log off?"
date: 2011-05-07
forum: Desktop Environments
---

### Post by meerpower on 2011-05-07
Hi folks,

I have a strange, kind of dumb problem, I hope I can make myself clear and you understand what I mean:
I have a fresh 64Bit installation of Xubuntu 11.04 on my workstation. When I do a "Log off" -> "Restart" the system logs my user off and I find myself at the login-screen. Same with "Shutdown", it doesn't shutdown or reboot, it just logs off. On the login-screen, there's also a shutdown/restart feature, that works fine ... but shutting down the system that way is sort of complicated and unnecessary, isn't it?

Am I doing something wrong here? I've never had problems like that with older Xubuntu Releases, do I need to configure something to make a "direct-shutdown" with a user logged-in?

Thanks alot guys, any help would be highly appreciated ...

---

### Post by Toz on 2011-05-07
Not sure if I can help find a solution, but it looks like a bug:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/711571](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/711571)
It would appear that X is crashing on xfce exit.

Can you post back your ~/.xsession-errors file?

---

### Post by Jagoly on 2011-05-10
The problem only affects the user menu (one in top right corner), and not the stander menu you get when the power button is pressed. Here are my X session errors files. I'm not sure which is relevant.
.xsession-errors.old
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
xfdesktop[1438]: starting up
GNOME_KEYRING_CONTROL=/tmp/keyring-VN8zRc
GNOME_KEYRING_CONTROL=/tmp/keyring-VN8zRc
SSH_AUTH_SOCK=/tmp/keyring-VN8zRc/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-VN8zRc
SSH_AUTH_SOCK=/tmp/keyring-VN8zRc/ssh

(polkit-gnome-authentication-agent-1:1450): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
xfce4-settings-helper: Another instance is already running. Leaving...
(xfce4-indicator-plugin:1483): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:1483): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:1483): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1483): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:1483): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:1483): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:1483): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:1483): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1483): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:1483): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:1483): Indicator-Application-DEBUG: Request current apps
(xfce4-indicator-plugin:1483): Indicator-Messages-DEBUG: new_application_item ("Pidgin Internet Messenger")
** (nm-applet:1469): DEBUG: old state indicates that this was not a disconnect 0

(xfce4-indicator-plugin:1483): Indicator-Application-WARNING **: Unable to get application list: Operation was cancelled
(xfce4-indicator-plugin:1483): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:1483): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:1483): Indicator-Sound-DEBUG: new_title_widget ("gmusicbrowser")
(xfce4-indicator-plugin:1483): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(xfce4-indicator-plugin:1483): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(xfce4-indicator-plugin:1483): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
(xfce4-indicator-plugin:1483): Indicator-Application-DEBUG: Building new application entry: :1.41  with icon: nm-no-connection at position 0
** (nm-applet:1469): DEBUG: foo_client_state_changed_cb
(xfce4-indicator-plugin:1483): Indicator-Messages-DEBUG: new_application_item ("(null)")
** (nm-applet:1469): DEBUG: foo_client_state_changed_cb

(xfdesktop:1438): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfdesktop:1438): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed

(xfdesktop:1438): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed

(xfdesktop:1438): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Error: No running window found
** Message: xfsm-shutdown-helper.c:1470: Using ConsoleKit to Restart
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
firefox-bin: Fatal IO error 2 (No such file or directory) on X server :0.0.
```

.xsession-errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
xfdesktop[1431]: starting up
GNOME_KEYRING_CONTROL=/tmp/keyring-KIbfZi
xfce4-settings-helper: Another instance is already running. Leaving...
GNOME_KEYRING_CONTROL=/tmp/keyring-KIbfZi
SSH_AUTH_SOCK=/tmp/keyring-KIbfZi/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-KIbfZi
SSH_AUTH_SOCK=/tmp/keyring-KIbfZi/ssh

(polkit-gnome-authentication-agent-1:1441): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
(xfce4-indicator-plugin:1486): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:1486): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:1486): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1486): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:1486): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:1486): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:1486): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:1486): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1486): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:1486): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:1486): Indicator-Application-DEBUG: Request current apps
** (nm-applet:1465): DEBUG: old state indicates that this was not a disconnect 0
(xfce4-indicator-plugin:1486): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:1486): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:1486): Indicator-Sound-DEBUG: new_title_widget ("gmusicbrowser")
(xfce4-indicator-plugin:1486): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(xfce4-indicator-plugin:1486): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(xfce4-indicator-plugin:1486): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
(xfce4-indicator-plugin:1486): Indicator-Messages-DEBUG: new_application_item ("Pidgin Internet Messenger")
** (nm-applet:1465): DEBUG: foo_client_state_changed_cb
(xfce4-indicator-plugin:1486): Indicator-Application-DEBUG: Building new application entry: :1.37  with icon: nm-stage02-connecting02 at position 0
(xfce4-indicator-plugin:1486): Indicator-Messages-DEBUG: new_application_item ("(null)")
** (nm-applet:1465): DEBUG: foo_client_state_changed_cb
Error: No running window found

(xfce4-terminal:1711): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
```

---

### Post by Toz on 2011-05-10
Looks like a confirmed bug: 
[https://bugzilla.xfce.org/show_bug.cgi?id=7442](https://bugzilla.xfce.org/show_bug.cgi?id=7442)

---

### Post by friv_livs on 2011-06-15
add the following line to /etc/X11/xinit/xinitrc:

```
ck-launch-session startxfce4
```

worked on radeon laptop with phoenix bios.

hope this helps.

---

### Post by mike555 on 2011-07-26
> **friv_livs said:**
> add the following line to /etc/X11/xinit/xinitrc:

```
ck-launch-session startxfce4
```

worked on radeon laptop with phoenix bios.

hope this helps.

   Worked on Xubuntu 11.04 for me,except I already had that line, I just removed the  #  in front of it (as root) and saved......

---

### Post by loukingjr on 2011-08-22
adding that line did not work for me.

---

### Post by peyre on 2011-09-08
> **friv_livs said:**
> add the following line to /etc/X11/xinit/xinitrc:

```
ck-launch-session startxfce4
```

worked on radeon laptop with phoenix bios.

hope this helps.

Hey, that worked on my system!  (Xubuntu 11.04 32-bit)

---

