---
title: "Gnome 3 Fallback Mode"
date: 2011-11-09
forum: Desktop Environments
---

### Post by Drone4four on 2011-11-09
How do I flip the switch in Gnome 3.2 to use fallback mode?

According to these two guides ([one]("http://youtu.be/6sVby2RIWE4"), [two]("http://www.dedoimedo.com/computers/gnome-3-fallback.html")), I am supposed to navigate to System Info --> Graphics &#8594; Select Forced Fallback Mode to ON.  However I don&#8217;t have a Forced Fallback Mode option in my System Info box.  See [here]("http://picpaste.com/pics/Screenshot_at_2011-11-09_19_49_47-eOzRqiZV.1320886239.png").  

I searched synaptic for &#8216;fallback&#8217; and there were many entries.  One of which is &#8216;gnome-session-fallback&#8217; that synaptic said was already installed.  So in a terminal I enter, ```
sudo gnome-session-fallback
```  Code whizzes by.  My Gnome 3.2 Desktop partially transforms into what almost looks like 2.32 and then the code in the terminal chokes.  Here is the full out put of that command:
```

gnull@oneiric:~$ sudo gnome-session-fallback
[sudo] password for gnull:
GNOME_KEYRING_CONTROL=/tmp/keyring-GEnCkm
GNOME_KEYRING_PID=6581
GNOME_KEYRING_CONTROL=/tmp/keyring-GEnCkm
SSH_AUTH_SOCK=/tmp/keyring-GEnCkm/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-GEnCkm
SSH_AUTH_SOCK=/tmp/keyring-GEnCkm/ssh
GPG_AGENT_INFO=/tmp/keyring-GEnCkm/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-GEnCkm
SSH_AUTH_SOCK=/tmp/keyring-GEnCkm/ssh
GPG_AGENT_INFO=/tmp/keyring-GEnCkm/gpg:0:1

** (gnome-settings-daemon:6579): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:6579): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
[1320887658,000,xklavier.c:xkl_engine_start_listen/]     The backend does not require manual layout management - but it is provided by the application
common-plugin-Message: checking whether we have a device for 4: yes
common-plugin-Message: checking whether we have a device for 5: yes
common-plugin-Message: checking whether we have a device for 6: yes
common-plugin-Message: checking whether we have a device for 7: yes
common-plugin-Message: checking whether we have a device for 8: yes
common-plugin-Message: checking whether we have a device for 9: yes
common-plugin-Message: checking whether we have a device for 10: yes

(gnome-settings-daemon:6579): media-keys-plugin-WARNING **: Grab failed for some keys, another application may already have access the them.

(gnome-settings-daemon:6579): clipboard-plugin-WARNING **: Clipboard manager is already running.

** (gnome-settings-daemon:6579): WARNING **: Failed to get session for pid: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6579'

(gnome-settings-daemon:6579): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

** (gnome-settings-daemon:6579): WARNING **: Failed to get session for pid: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6579'
Window manager warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.

(polkit-gnome-authentication-agent-1:6614): polkit-gnome-1-WARNING **: Unable to determine the session we are in: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6614'

ERROR: Invalid display device DFP-2 specified on line 47 of configuration file '/home/gnull/.nvidia-settings-rc' (the currently enabled display devices are DFP-0 on oneiric:0.0).


ERROR: Invalid display device DFP-2 specified on line 48 of configuration file '/home/gnull/.nvidia-settings-rc' (the currently enabled display devices are DFP-0 on oneiric:0.0).


ERROR: Invalid display device DFP-2 specified on line 49 of configuration file '/home/gnull/.nvidia-settings-rc' (the currently enabled display devices are DFP-0 on oneiric:0.0).


ERROR: Invalid display device DFP-2 specified on line 50 of configuration file '/home/gnull/.nvidia-settings-rc' (the currently enabled display devices are DFP-0 on oneiric:0.0).


ERROR: Invalid display device DFP-2 specified on line 51 of configuration file '/home/gnull/.nvidia-settings-rc' (the currently enabled display devices are DFP-0 on oneiric:0.0).


ERROR: The attribute 'XVideoSyncToDisplay' specified on line 57 of configuration file '/home/gnull/.nvidia-settings-rc' cannot be assigned the value of DFP-2 (the currently enabled display devices are DFP-0 on oneiric:0.0).

** (gnome-fallback-mount-helper:6618): DEBUG: Starting automounting manager
Loading configuration plugins
blueman-applet version 1.22 starting
Stale PID, overwriting
Initializing nautilus-gdu extension
Using gconf config backend
Using gconf config backend
** Message: applet now removed from the notification area

** (nm-applet:6616): WARNING **: Failed to register as an agent: (32) No session found for uid 0

** (gnome-fallback-mount-helper:6618): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6618'
** (gnome-fallback-mount-helper:6618): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:6618): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:6618): DEBUG: Screensaver GetActive() returned 0
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Traceback (most recent call last):
 File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
 File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher
Using gconf config backend
** Message: using fallback from indicator to GtkStatusIcon
Using gconf config backend

(nautilus:6617): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:6617): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed
Using gconf config backend
Using gconf config backend
Deleting plugin instance <blueman.plugins.applet.PulseAudio.PulseAudio object at 0x98f4c2c>
Using gconf config backend

(gnome-panel:6601): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x8d8dd20'
** Message: applet now embedded in the notification area

(gnome-settings-daemon:6579): Gdk-WARNING **: The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
 (Details: serial 2280 error_code 8 request_code 3 minor_code 0)
 (Note to programmers: normally, X errors are reported asynchronously;
  that is, you will receive the error a while after causing it.
  To debug your program, run it with the --sync command line
  option to change this behavior. You can then get a meaningful
  backtrace from your debugger if you break on the gdk_x_error() function.)


** (gnome-settings-daemon:6659): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:6659): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

(gnome-settings-daemon:6659): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -23 and height 32

** (gnome-settings-daemon:6659): WARNING **: Failed to get session for pid: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6659'

(gnome-settings-daemon:6659): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

** (gnome-settings-daemon:6659): WARNING **: Failed to get session for pid: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6659'
[1320887662,000,xklavier.c:xkl_engine_start_listen/]     The backend does not require manual layout management - but it is provided by the application
common-plugin-Message: checking whether we have a device for 4: yes
common-plugin-Message: checking whether we have a device for 5: yes
common-plugin-Message: checking whether we have a device for 6: yes
common-plugin-Message: checking whether we have a device for 7: yes
common-plugin-Message: checking whether we have a device for 8: yes
common-plugin-Message: checking whether we have a device for 9: yes
common-plugin-Message: checking whether we have a device for 10: yes

(gnome-settings-daemon:6659): media-keys-plugin-WARNING **: Grab failed for some keys, another application may already have access the them.

(gnome-settings-daemon:6659): clipboard-plugin-WARNING **: Clipboard manager is already running.
** (process:6673): DEBUG: Telepathy Indicator started

** (gnome-screensaver:6674): WARNING **: Screensaver already running in this session
Failure: Module initalization failed

** (gnome-user-share:6685): WARNING **: gnome-user-share cannot be started as root for security reasons.

(process:6686): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:6686): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (update-notifier:6696): WARNING **: not starting for system user



```

How do I make my Gnome 3 look like Gnome 2?

---

### Post by cbowman57 on 2011-11-09
Unless you have autologin enabled you should be able to choose your desktop from the login screen.

---

### Post by 3Miro on 2011-11-09
If you logout and on the login screen there should be a gear icon to the left of your username. You should be able to select the gear icon and chose Gnome-classic (No Effects), which is gnome-fallback.

---

### Post by Drone4four on 2011-11-10
Selecting Gnome(Classic) at GDM and then logging in makes my Desktop look more like Gnome 2.32, but I can't edit the contents of my panel.  For example I can't add launchers.  Also, I can't move the date and time from the center of the panel all the way over to the left.  What gives?

---

### Post by cbowman57 on 2011-11-10
alt+r-click

---

### Post by 3Miro on 2011-11-10
> **Drone4four said:**
> Selecting Gnome(Classic) at GDM and then logging in makes my Desktop look more like Gnome 2.32, but I can't edit the contents of my panel.  For example I can't add launchers.  Also, I can't move the date and time from the center of the panel all the way over to the left.  What gives?

Ubuntu is no longer using GDM, but LDM. 

Gnome-fallback is not exactly like Gnome 2, many things are different. Look at cbowman57's post.

---

