---
title: "Ubuntu freezes after about one minute"
date: 2009-05-07
forum: General Help
---

### Post by FrederikVds on 2009-05-07
Hi,

Since the day before yesterday, Ubuntu Jaunty (+security, updates, proposed and backports) freezes about one minute after logging in. I can move the mouse, but nothing else works (except Ctrl-Alt-Backspace, Ctrl-Alt-F5, ...). This only happens after a graphical log-in, on both Gnome and KDE.
I have no idea where to look. Could anyone give me any hints? I've tried various things already (like updating the kernel, which seemed to work yesterday, but since this morning I have the same problem again). I've also searched my logs but I have no idea what to look for.

Thanks,
Frederik

---

### Post by Wayne_V on 2009-05-07
Try ^-Alt-F1 and get to a console login.  Run top to see if something is hogging the CPU.

---

### Post by FrederikVds on 2009-05-07
Nothing is using more than 1% CPU...

---

### Post by Wayne_V on 2009-05-07
Not sure where to go then.  You could check "more ~/.xsession-errors"

Maybe try turning compiz off (Applications->Accessories->Compiz Switch).  You may have to "sudo apt-get install compiz-switch" first.

Maybe, in the console window (^-Alt-F1) run "tail -f /var/log/{dmesg,messages,*log} | more" and then ^-Alt-F7 to log in graphically and then go back to the console to see if there are any useful error messages

---

### Post by ssdt on 2009-05-07
Is it like Fedora which refeshed Kernal every 10 minutes making your computer slow?

---

### Post by FrederikVds on 2009-05-07
It's not just slow, it doesn't respond at all.
compiz is always off, it doesn't work because I have two monitors.

.xsession-errors contains this, don't know what to look for:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=nl_BE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/frederik/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-W9wflQ/socket
SSH_AUTH_SOCK=/tmp/keyring-W9wflQ/socket.ssh

(gnome-settings-daemon:3688): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Windowmanager waarschuwing: Lezen van opgeslagen sessiebestand /home/frederik/.config/metacity/sessions/102974fe34edee8be9124171010329500500000034960029.ms mislukt: Openen van bestand /home/frederik/.config/metacity/sessions/102974fe34edee8be9124171010329500500000034960029.ms is mislukt: Bestand of map bestaat niet
** (gnome-panel:3694): DEBUG: Adding applet 0.
** (gnome-panel:3694): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3694): DEBUG: Adding applet 1.
Failure: Module initalization failed
x-session-manager[3496]: WARNING: Could not launch application 'hplip-systray.desktop': Unable to start application: Uitvoeren van dochterproces hp-systray is mislukt (Bestand of map bestaat niet)
x-session-manager[3496]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Uitvoeren van dochterproces /usr/lib/gnome-volume-manager/gnome-volume-manager is mislukt (Bestand of map bestaat niet)
** (gnome-panel:3694): DEBUG: Adding applet 2.
** (gnome-panel:3694): DEBUG: Adding applet 3.
** (gnome-panel:3694): DEBUG: Adding applet 4.
** (gnome-panel:3694): DEBUG: Adding applet 5.
** (gnome-panel:3694): DEBUG: Adding applet 6.
** (gnome-panel:3694): DEBUG: Adding applet 7.
** (gnome-panel:3694): DEBUG: Adding applet 8.

(gnome-panel:3694): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:3694): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3694): DEBUG: Adding applet 9.
** (gnome-panel:3694): DEBUG: Adding applet 10.

** (nautilus:3695): WARNING **: Unable to add monitor: Niet ondersteund
** (gnome-panel:3694): DEBUG: Adding applet 11.

(gnome-panel:3694): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' gaf fout 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Bestand of map bestaat niet
Please ask your system administrator to enable user sharing.

gnome-settings-daemon: Fatal IO error 104 (Verbinding is weggevallen) on X server :0.0.
gnome-panel: Fatal IO error 104 (Verbinding is weggevallen) on X server :0.0.
Windowmanager waarschuwing: Fatale IO-fout 11 (Hulpbron is tijdelijk onbeschikbaar) op display :0.0.
x-session-manager: Fatal IO error 11 (Hulpbron is tijdelijk onbeschikbaar) on X server :0.0.
nautilus: Fatal IO error 104 (Verbinding is weggevallen) on X server :0.0.
Xsession: X session started for frederik at do mei  7 18:09:13 CEST 2009
Setting IM through im-switch for locale=nl_BE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/frederik/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-lC2Xyt/socket
SSH_AUTH_SOCK=/tmp/keyring-lC2Xyt/socket.ssh
GNOME_KEYRING_PID=6636

(gnome-settings-daemon:6635): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Windowmanager waarschuwing: Lezen van opgeslagen sessiebestand /home/frederik/.config/metacity/sessions/10f2735ad577d5c1f0124171255426361600000065670029.ms mislukt: Openen van bestand /home/frederik/.config/metacity/sessions/10f2735ad577d5c1f0124171255426361600000065670029.ms is mislukt: Bestand of map bestaat niet
** (gnome-panel:6642): DEBUG: Adding applet 0.
** (gnome-panel:6642): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:6642): DEBUG: Adding applet 1.
Failure: Module initalization failed
x-session-manager[6567]: WARNING: Could not launch application 'hplip-systray.desktop': Unable to start application: Uitvoeren van dochterproces hp-systray is mislukt (Bestand of map bestaat niet)
x-session-manager[6567]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Uitvoeren van dochterproces /usr/lib/gnome-volume-manager/gnome-volume-manager is mislukt (Bestand of map bestaat niet)
** (gnome-panel:6642): DEBUG: Adding applet 2.
** (gnome-panel:6642): DEBUG: Adding applet 3.
** (gnome-panel:6642): DEBUG: Adding applet 4.
** (gnome-panel:6642): DEBUG: Adding applet 5.
** (gnome-panel:6642): DEBUG: Adding applet 6.
** (gnome-panel:6642): DEBUG: Adding applet 7.

(gnome-panel:6642): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

(gnome-panel:6642): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:6642): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:6642): DEBUG: Adding applet 8.
** (gnome-panel:6642): DEBUG: Adding applet 9.
** (gnome-panel:6642): DEBUG: Adding applet 10.
** (gnome-panel:6642): DEBUG: Adding applet 11.

** (nautilus:6643): WARNING **: Unable to add monitor: Niet ondersteund
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' gaf fout 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Bestand of map bestaat niet
Please ask your system administrator to enable user sharing.

gnome-settings-daemon: Fatal IO error 11 (Hulpbron is tijdelijk onbeschikbaar) on X server :0.0.

** (gnome-screensaver:6710): WARNING **: Kan display  niet opnenen
x-session-manager: Fatal IO error 104 (Verbinding is weggevallen) on X server :0.0.
pidgin: Fatal IO error 104 (Verbinding is weggevallen) on X server :0.0.
Xsession: X session started for frederik at do mei  7 19:51:48 CEST 2009
Setting IM through im-switch for locale=nl_BE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/frederik/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-DhZief/socket
SSH_AUTH_SOCK=/tmp/keyring-DhZief/socket.ssh
GNOME_KEYRING_PID=13457

(gnome-settings-daemon:13456): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Windowmanager waarschuwing: Lezen van opgeslagen sessiebestand /home/frederik/.config/metacity/sessions/1039c1c6f69e5376dc124171870985596800000133790029.ms mislukt: Openen van bestand /home/frederik/.config/metacity/sessions/1039c1c6f69e5376dc124171870985596800000133790029.ms is mislukt: Bestand of map bestaat niet
** (gnome-panel:13463): DEBUG: Adding applet 0.
** (gnome-panel:13463): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:13463): DEBUG: Adding applet 1.
Failure: Module initalization failed
x-session-manager[13379]: WARNING: Could not launch application 'hplip-systray.desktop': Unable to start application: Uitvoeren van dochterproces hp-systray is mislukt (Bestand of map bestaat niet)
x-session-manager[13379]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Uitvoeren van dochterproces /usr/lib/gnome-volume-manager/gnome-volume-manager is mislukt (Bestand of map bestaat niet)
** (gnome-panel:13463): DEBUG: Adding applet 2.
** (gnome-panel:13463): DEBUG: Adding applet 3.
** (gnome-panel:13463): DEBUG: Adding applet 4.
** (gnome-panel:13463): DEBUG: Adding applet 5.

(gnome-panel:13463): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:13463): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:13463): DEBUG: Adding applet 6.
** (gnome-panel:13463): DEBUG: Adding applet 7.
** (gnome-panel:13463): DEBUG: Adding applet 8.
** (gnome-panel:13463): DEBUG: Adding applet 9.
** (gnome-panel:13463): DEBUG: Adding applet 10.
** (gnome-panel:13463): DEBUG: Adding applet 11.

(gnome-panel:13463): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

** (nautilus:13464): WARNING **: Unable to add monitor: Niet ondersteund
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' gaf fout 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Bestand of map bestaat niet
Please ask your system administrator to enable user sharing.

Windowmanager waarschuwing: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1600048 (Contactenl)
Windowmanager waarschuwing: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
x-session-manager: Fatal IO error 11 (Hulpbron is tijdelijk onbeschikbaar) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Hulpbron is tijdelijk onbeschikbaar) on X server :0.0.

** (gnome-screensaver:13532): WARNING **: Kan display  niet opnenen
Xsession: X session started for frederik at Thu May  7 20:06:12 CEST 2009
Setting IM through im-switch for locale=en.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/frederik/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.

(process:15356): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(process:15356): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(process:15408): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(process:15420): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
GNOME_KEYRING_SOCKET=/tmp/keyring-mQEh1n/socket
SSH_AUTH_SOCK=/tmp/keyring-mQEh1n/socket.ssh
GNOME_KEYRING_PID=15425

(process:15423): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(gnome-settings-daemon:15424): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Locale not understood by C library, internationalization will not work

(metacity:15430): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Window manager warning: Failed to read saved session file /home/frederik/.config/metacity/sessions/10de37329eeba5872a124171957415776200000153560029.ms: Failed to open file '/home/frederik/.config/metacity/sessions/10de37329eeba5872a124171957415776200000153560029.ms': No such file or directory

(gnome-panel:15431): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(gnome-panel:15431): Gdk-WARNING **: locale not supported by C library
** (gnome-panel:15431): DEBUG: Adding applet 0.
** (gnome-panel:15431): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:15431): DEBUG: Adding applet 1.

(nautilus:15432): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(process:15436): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(process:15444): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(process:15438): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Failure: Module initalization failed
x-session-manager[15356]: WARNING: Could not launch application 'hplip-systray.desktop': Unable to start application: Failed to execute child process "hp-systray" (No such file or directory)
x-session-manager[15356]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory)

(process:15440): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
** (gnome-panel:15431): DEBUG: Adding applet 2.
** (gnome-panel:15431): DEBUG: Adding applet 3.
** (gnome-panel:15431): DEBUG: Adding applet 4.

(gnome-power-manager:15452): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(update-notifier:15457): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
** (gnome-panel:15431): DEBUG: Adding applet 5.

(gnome-power-manager:15452): Gdk-WARNING **: locale not supported by C library

(update-notifier:15457): Gdk-WARNING **: locale not supported by C library
** (gnome-panel:15431): DEBUG: Adding applet 6.

(gnome-panel:15431): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:15431): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.

(process:15437): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
** (gnome-panel:15431): DEBUG: Adding applet 7.
** (gnome-panel:15431): DEBUG: Adding applet 8.
** (gnome-panel:15431): DEBUG: Adding applet 9.
** (gnome-panel:15431): DEBUG: Adding applet 10.
** (gnome-panel:15431): DEBUG: Adding applet 11.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1600048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (nautilus:15432): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(process:15504): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
x-session-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

** (gnome-screensaver:15504): WARNING **: Cannot open display: 
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

```

I've looked at the output of tail -f /var/log/{dmesg,messages,*log} but I have no idea what to look for.

---

