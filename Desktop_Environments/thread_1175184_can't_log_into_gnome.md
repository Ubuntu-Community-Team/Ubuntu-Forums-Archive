---
title: "can't log into gnome"
date: 2009-05-31
forum: Desktop Environments
---

### Post by rmmartins on 2009-05-31
Guys, I've looked into every corner of the internet, to no avail. I can't log into gnome. 

GDM comes up, I enter my login info, gnome-panel appears for one second and then it's all blank.

When I switch to alt+f1, it's all blinking very fast, but i can see the text. I kill X and then I get GDM again.

I can log into failsafe terminal, then I can run metacity and gnome-panel OK (that's where I am now). gnome-terminal, for example, won't run. If I try running x-session-manager, the screen blanks again, like before. So i think x-session-manager is the problem (although i dont know exactly what it does).

I re-installed lots of stuff: gdm, gnome-session, ubuntu-desktop; deleted .local, .profile, .gnome*, nothing.

So I give you my .xsession-errors, and I hope somebody can help me.

Thanks in advance!

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-qJiiRf/socket
SSH_AUTH_SOCK=/tmp/keyring-qJiiRf/socket.ssh

(gnome-settings-daemon:4070): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
xrandr: cannot find mode 1680x1050
Failure: Module initalization failed
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/rafael/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/rafael/.config/tracker/tracker.cfg'
** (nm-applet:4177): DEBUG: applet_common_device_state_changed
** (nm-applet:4177): DEBUG: applet_common_device_state_changed
** (nm-applet:4177): DEBUG: old state indicates that this was not a disconnect 0
** (gnome-panel:4144): DEBUG: Adding applet 0.
** (gnome-panel:4144): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4144): DEBUG: Adding applet 1.
** (gnome-panel:4144): DEBUG: Adding applet 2.
** (gnome-panel:4144): DEBUG: Adding applet 3.
** (gnome-panel:4144): DEBUG: Adding applet 4.
** (gnome-panel:4144): DEBUG: Adding applet 5.
** (gnome-panel:4144): DEBUG: Adding applet 6.
** (gnome-panel:4144): DEBUG: Adding applet 7.
** (gnome-panel:4144): DEBUG: Adding applet 8.

** (nautilus:4145): WARNING **: Unable to add monitor: Not supported
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
CachingBackend: Loading instances from cache
CachingBackend: Loading <ClearCalendar1>
No global tempdir found, creating new one.
Temp directory /tmp/screenlets created.
Creating new entry for ClearCalendarScreenlet in /tmp/screenlets/screenlets.rafael.running

(awn-applets-migration:4261): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Loading instances in: /home/rafael/.config/Screenlets/ClearCalendar/default/
File: ClearCalendar1.ini
Screen is composited.
LOADED : /usr/share/applications/awn-manager.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
/home/rafael/.config/Screenlets/ClearCalendar/default/ClearCalendar1
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/ClearCalendar/themes/default
Set options in ClearCalendarScreenlet
Screenlet has been initialized.
Restored instances from session 'default' ...
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/rafael/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/rafael/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/rafael/.local/share/tracker/trackerd.log'
** (gnome-panel:4144): DEBUG: Adding applet 9.
** (gnome-panel:4144): DEBUG: Adding applet 10.
** (gnome-panel:4144): DEBUG: Adding applet 11.

(gnome-panel:4144): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4144): DEBUG: Adding applet 12.
OK

(gnome-panel:4144): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
OK
evolution-alarm-notify-Message: Setting timeout for 82399 1243900800 1243818401
evolution-alarm-notify-Message:  Mon Jun  1 21:00:00 2009

evolution-alarm-notify-Message:  Sun May 31 22:06:41 2009

OK
OK
OK
** (update-notifier:4165): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
  PID TTY          TIME CMD
 4040 ?        00:00:00 pulseaudio
4144
** (update-notifier:4165): DEBUG: crashreport_check

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 6907 requests (6904 known processed) with 7 events remaining.

gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

---

### Post by rmmartins on 2009-06-01
Sorry, but "bump". Can anyone look at my error logs please??

---

### Post by rmmartins on 2009-06-01
Ok, so the problem seems to be with xrandr, since I purged 'x11-xserver-tools' and now it works (even though i get an error about xrdb).

There is that 'xrandr: cannot find mode 1680x1050' line.. does anyone know where xrandr keep those configs?

Thanks.

---

### Post by rmmartins on 2009-06-01
Ok, solved the problem.

There was a my-stupid-self-made script setting xrandr on startup.

Bash me.

---

