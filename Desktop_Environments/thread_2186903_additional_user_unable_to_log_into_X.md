---
title: "additional user unable to log into X"
date: 2013-11-09
forum: Desktop Environments
---

### Post by edgreenberg on 2013-11-09
I have a working Ubuntu-Gnome installation, which I generally use in Flashback mode. 

I created a second user for my visiting sister, and we could not log in.  We got stuck at the grey Ubuntu Gnome screen after entering the password. 

I ssh'd into the machine and did a 'ps fax' and got this (snippet):

```
  939 ?        Ssl    0:00 gdm
23368 ?        Sl     0:00  \_ /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Displays/_0
23373 tty7     Ssl+   0:01      \_ /usr/bin/X :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-QsYfUh/database -seat seat0 -nolisten tcp vt7
23720 ?        Sl     0:00      \_ gdm-session-worker [pam/gdm-password]
23787 ?        Ss     0:00          \_ init --user
23845 ?        Ss     0:00              \_ ssh-agent
```

Review of the syslog at the time of login shows:

```
Nov  9 07:54:13 arthur gdm-password][23720]: AccountsService: SetLanguage call failed: GDBus.Error:org.freedesktop.Accounts.Error.Failed: not access to HOME yet so 
language not saved
Nov  9 07:54:13 arthur colord: device removed: xrandr-Dell-DELL 1907FP-DC32366KBF34
Nov  9 07:54:13 arthur colord: device removed: xrandr-Dell-DELL 1907FP-DC323662G676
Nov  9 07:54:13 arthur colord: Profile removed: icc-81787ac31be422dcefcb5353ddb5e897
Nov  9 07:54:13 arthur colord: Profile removed: icc-9cb75b82521d835a8d6fad1d60c2deec
Nov  9 07:54:13 arthur gdm-simple-slave[23368]: Failed to remove slave program access to the display. Trying to proceed.
Nov  9 07:54:13 arthur gdm-simple-slave[23368]: Child process -23435 was already dead.
Nov  9 08:00:01 arthur CRON[24064]: (edg) CMD (/usr/bin/aplay /home/edg/bells/8bells.wav)
Nov  9 08:00:01 arthur CRON[24066]: (edg) CMD (/usr/bin/aplay /home/edg/bells/1bells.wav)
Nov  9 08:00:01 arthur pulseaudio[24072]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbu
s-daemon without a $DISPLAY for X11
Nov  9 08:00:01 arthur pulseaudio[24072]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon 
without a $DISPLAY for X11
Nov  9 08:00:01 arthur pulseaudio[24076]: [pulseaudio] pid.c: Daemon already running.
Nov  9 08:00:03 arthur CRON[24063]: (CRON) info (No MTA installed, discarding output)
Nov  9 08:00:07 arthur CRON[24062]: (CRON) info (No MTA installed, discarding output)
```

So it looks like it got stuck somewhere.

My working login has a process tree that looks like this...

```
  951 ?        Ssl    0:00 gdm
 1082 ?        Sl     0:00  \_ /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Displays/_0
 1088 tty7     Ssl+   9:54      \_ /usr/bin/X :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-szYC4e/database -seat seat0 -nolisten tcp vt7
 1829 ?        Sl     0:00      \_ gdm-session-worker [pam/gdm-password]
 1875 ?        Ss     0:00          \_ init --user
 1934 ?        Ss     0:00              \_ ssh-agent
 1937 ?        Ss     0:03              \_ dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-ySh2tdnmgj
 1942 ?        Ss     0:00              \_ upstart-event-bridge
 1967 ?        Ssl    0:02              \_ /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 1969 ?        Sl     0:00              \_ /usr/lib/at-spi2-core/at-spi-bus-launcher
 1973 ?        S      0:00              |   \_ /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
 1976 ?        Sl     0:00              \_ /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 1998 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfsd
 2000 ?        Ssl    0:00              \_ gnome-session --session=gnome-fallback
 2171 ?        Sl     0:32              |   \_ metacity
 2177 ?        Sl     1:09              |   \_ gnome-panel
12802 ?        Sl     6:33              |   |   \_ /usr/lib/firefox/firefox
16098 ?        Sl     0:04              |   |   \_ gnome-terminal
16104 ?        S      0:00              |   |   |   \_ gnome-pty-helper
16105 pts/0    Ss     0:00              |   |   |   \_ bash
18921 pts/0    S+     0:00              |   |   |   |   \_ less
16254 pts/2    Ss+    0:00              |   |   |   \_ bash
19362 pts/5    Ss     0:00              |   |   |   \_ bash
19484 pts/5    R+     0:00              |   |   |       \_ ps fax
18630 ?        Sl     0:04              |   |   \_ gnome-control-center --overview
19132 ?        Sl     0:17              |   |   \_ /usr/lib/thunderbird/thunderbird
 2189 ?        Sl     0:00              |   \_ /usr/lib/notification-daemon/notification-daemon
 2193 ?        Sl     0:04              |   \_ /usr/bin/pidgin
18928 ?        Z      0:00              |   |   \_ [pidgin] <defunct>
 2195 ?        S      2:52              |   \_ /usr/bin/gkrellm
 2196 ?        Ssl    0:00              |   \_ /usr/bin/python /usr/bin/hp-systray -x
 2219 ?        S      0:03              |   |   \_ /usr/bin/python /usr/bin/hp-systray -x
 2220 ?        S      0:01              |   |       \_ /usr/bin/python /usr/bin/hp-systray -x
 2197 ?        Sl     0:00              |   \_ /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 2200 ?        Sl     0:00              |   \_ /usr/lib/tracker/tracker-store
 2201 ?        SNl    0:00              |   \_ /usr/lib/tracker/tracker-miner-fs
 2202 ?        Sl     0:14              |   \_ nautilus -n
 2206 ?        Sl     0:00              |   \_ /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
 2207 ?        Sl     0:23              |   \_ /usr/bin/python /usr/bin/autokey-gtk
 2210 ?        Sl     0:00              |   \_ /usr/bin/python /usr/share/gnome-manual-duplex/gmd-applet-3.py run-in-tray
 2211 ?        Sl     2:45              |   \_ /usr/bin/python /usr/bin/nagstamon
14914 ?        Z      0:00              |   |   \_ [sh] <defunct>
 2218 ?        Sl     0:05              |   \_ mono /usr/lib/tomboy/Tomboy.exe
 2221 ?        Sl     0:00              |   \_ nm-applet
 2426 ?        Sl     0:00              |   \_ zeitgeist-datahub
 2428 ?        Sl     0:32              |   \_ gnome-screensaver
 2636 ?        Sl     0:00              |   \_ /usr/lib/evolution/3.8/evolution-alarm-notify
 2768 ?        Sl     0:00              |   \_ update-notifier
 2840 ?        Sl     0:00              |   \_ /usr/lib/i386-linux-gnu/deja-dup/deja-dup-monitor
 2020 ?        S      0:00              \_ upstart-file-bridge --daemon --user
 2023 ?        S      0:00              \_ upstart-dbus-bridge --daemon --system --user --bus-name system
 2025 ?        S      0:01              \_ upstart-dbus-bridge --daemon --session --user --bus-name session
 2085 ?        Sl     0:00              \_ /usr/lib/dconf/dconf-service
 2092 ?        S<l    0:13              \_ /usr/bin/pulseaudio --start --log-target=syslog
 2094 ?        Sl     0:00              \_ /usr/lib/gvfs//gvfsd-fuse -f /run/user/1000/gvfs
 2108 ?        Sl     0:00              \_ /usr/lib/gnome-settings-daemon/gsd-printer
 2111 ?        Sl     0:00              \_ /usr/bin/ibus-daemon --replace --xim --panel disable
 2145 ?        Sl     0:00              |   \_ /usr/lib/ibus/ibus-dconf
 2174 ?        Sl     0:00              |   \_ /usr/lib/ibus/ibus-engine-simple
 2147 ?        Sl     0:00              \_ /usr/lib/ibus/ibus-x11 --kill-daemon
 2181 ?        S      0:00              \_ /usr/lib/i386-linux-gnu/gconf/gconfd-2
 2203 ?        Ssl    0:10              \_ /home/edg/.dropbox-dist/dropbox
 2228 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfs-udisks2-volume-monitor
 2248 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfs-mtp-volume-monitor
 2253 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 2260 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfs-afc-volume-monitor
 2265 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfs-goa-volume-monitor
 2269 ?        Sl     0:00              \_ /usr/lib/gnome-online-accounts/goa-daemon
 2272 ?        Sl     0:00              \_ /usr/lib/gnome-applets/trashapplet
 2279 ?        Sl     0:12              \_ /usr/lib/gnome-applets/multiload-applet-2
 2283 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfsd-trash --spawner :1.7 /org/gtk/gvfs/exec_spaw/0
 2296 ?        Sl     0:00              \_ /usr/bin/python /usr/share/gnome-manual-duplex/gmd-applet-3.py
 2308 ?        S      0:00              \_ /usr/lib/gamin/gam_server
 2338 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfsd-burn --spawner :1.7 /org/gtk/gvfs/exec_spaw/1
 2419 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfsd-metadata
 2422 ?        Sl     0:05              \_ /usr/lib/i386-linux-gnu/indicator-applet-complete
 2433 ?        Sl     0:00              \_ /usr/bin/zeitgeist-daemon
 2443 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/zeitgeist-fts
 2454 ?        S      0:00              |   \_ /bin/cat
 2471 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-sync/indicator-sync-service
 2474 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-sound/indicator-sound-service
 2476 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
 2478 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-printers-service
 2479 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-messages/indicator-messages-service
 2481 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-keyboard-service --use-gtk --use-bamf
 2483 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-session/indicator-session-service
 2484 ?        Sl     0:00              \_ /usr/lib/i386-linux-gnu/indicator-application-service
 2486 ?        Sl     0:03              \_ /usr/lib/i386-linux-gnu/indicator-power/indicator-power-service
 2647 ?        Sl     0:00              \_ /usr/lib/evolution/evolution-source-registry
 2653 ?        Sl     0:00              \_ /usr/lib/evolution/evolution-calendar-factory
 5888 ?        Sl     0:00              \_ /usr/lib/evolution/evolution-addressbook-factory
16503 ?        SLl    0:00              \_ /usr/lib/gvfs/gvfsd-smb --spawner :1.7 /org/gtk/gvfs/exec_spaw/2
16849 ?        Sl     0:43              \_ rhythmbox
17106 ?        Sl     0:00              \_ /usr/lib/gvfs/gvfsd-http --spawner :1.7 /org/gtk/gvfs/exec_spaw/3
```

Any idea how to free this up? 

Thanks

---

