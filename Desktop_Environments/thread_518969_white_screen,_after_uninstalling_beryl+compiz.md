---
title: "white screen, after uninstalling beryl+compiz"
date: 2007-08-06
forum: Desktop Environments
---

### Post by Aesir09 on 2007-08-06
apparently even after uninstalling beryl and compiz (which i though was that problem, i am still receiving the white screen of death)'

i have uninstalled beryl and compiz and apparently the ubuntu desktop effects

hmmm...?

here are my startup processes:

[C]dominik@ubuntu:~$ ps U dominik
  PID TTY      STAT   TIME COMMAND
 5752 ?        Ssl    0:00 /usr/bin/gnome-session --failsafe
 5766 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 6
 5769 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5774 ?        S      0:00 dbus-launch --autolaunch 21e05cb70483ace921e2d20046b5
 5775 ?        Ss     0:00 dbus-daemon --fork --print-address 18 --print-pid 20
 5776 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 6 --print-add
 5778 ?        Sl     0:00 /usr/lib/control-center/gnome-settings-daemon
 5785 ?        Ss     0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -sp
 5786 ?        S      0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 22
 5790 ?        S      0:01 /usr/bin/metacity --sm-client-id=default0
 5793 ?        S      0:01 gnome-panel --sm-client-id default1
 5796 ?        S      0:00 nautilus --no-default-window --sm-client-id default2
 5802 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5803 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5811 ?        S      0:00 update-notifier
 5814 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 5815 ?        Sl     0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
 5819 ?        S      0:00 nm-applet --sm-disable
 5820 ?        S      0:00 gnome-cups-icon --sm-client-id default3
 5821 ?        Ss     0:00 gnome-power-manager
 5836 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 5838 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5881 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5889 ?        Ss     0:00 gnome-screensaver
 5951 ?        Sl     0:01 gnome-terminal
 5957 ?        Sl     0:28 /usr/lib/firefox/firefox-bin
 5958 ?        S      0:00 gnome-pty-helper
 5996 ?        Z      0:00 [netstat] <defunct>
 6019 ?        S      0:21 gnome-system-monitor
 6673 pts/1    Ss     0:00 bash
 6693 pts/1    R+     0:00 ps U dominik
[/C]








**PS: I AM LOGGED INTO MY USER ON FAILSAFE GNOME**

---

### Post by todh on 2007-08-07
Just had the same problem and fixed it.  Check it out at the end of this post.

[http://ubuntuforums.org/showthread.php?p=3146644#post3146644](http://ubuntuforums.org/showthread.php?p=3146644#post3146644)

---

