---
title: "gnome slow to log in... here are my logs, help :)"
date: 2008-12-04
forum: Desktop Environments
---

### Post by graysky on 2008-12-04
I posted a thread a few days ago trying to figure out why it takes a good 20 sec for my desktop to display when I log into Gnome under any of my users (link to thread [here](http://www.gs1.ubuntuforums.org/showthread.php?t=1000147)).  I loaded up gnome-system-log and found a number of errors that might be affecting the speed.  I'd appreciate suggestions from folks.  Thanks in advance!

Intrepid amd64 (auto updates enabled).

**auth.log**
```
Dec  4 15:55:25 wire gdm[7244]: pam_unix(gdm:session): session opened for user squeeze by (uid=0)
Dec  4 15:55:25 wire gdm[7244]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :20
Dec  4 15:55:25 wire gdm[7244]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Dec  4 15:55:25 wire gdm[7244]: Autolaunch error: X11 initialization failed.
Dec  4 15:55:25 wire gdm[7244]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Dec  4 15:55:25 wire gdm[7244]: Autolaunch error: X11 initialization failed.
Dec  4 15:55:25 wire gdm[7244]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Dec  4 15:55:25 wire gdm[7244]: Autolaunch error: X11 initialization failed.
Dec  4 15:55:25 wire gdm[7244]: )
Dec  4 15:55:25 wire gnome-keyring-daemon[7297]: Couldn't unlock login keyring with provided password
Dec  4 15:55:25 wire gnome-keyring-daemon[7297]: Failed to unlock login on startup
Dec  4 15:55:54 wire gdm[7244]: pam_unix(gdm:session): session closed for user squeeze
Dec  4 15:55:59 wire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring

```

**daemon.log**
```
Dec  4 15:55:21 wire acpid: client connected from 7247[0:0] 
Dec  4 15:55:21 wire acpid: client connected from 7247[0:0] 
Dec  4 15:55:22 wire gdmgreeter[7288]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Dec  4 15:55:25 wire x-session-manager[7307]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Dec  4 15:55:35 wire x-session-manager[7307]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Dec  4 15:55:45 wire x-session-manager[7307]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
```

**kern.log**
```
Dec  4 15:55:54 wire kernel: [ 1476.414554] compiz.real[7533] trap stack segment ip:41024e sp:7fff3f344170 error:0
```

**messages**
```
Dec  4 15:55:25 wire pulseaudio[7428]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  4 15:55:25 wire pulseaudio[7430]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  4 15:55:25 wire pulseaudio[7430]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  4 15:55:54 wire kernel: [ 1476.414554] compiz.real[7533] trap stack segment ip:41024e sp:7fff3f344170 error:0
Dec  4 15:55:55 wire bonobo-activation-server (squeeze-7670): could not associate with desktop session: Failed to connect to socket /tmp/dbus-7U8HV8f99O: Connection refused
```

**syslog**
```
Dec  4 15:55:21 wire acpid: client connected from 7247[0:0] 
Dec  4 15:55:21 wire acpid: client connected from 7247[0:0] 
Dec  4 15:55:22 wire gdmgreeter[7288]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Dec  4 15:55:25 wire pulseaudio[7428]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  4 15:55:25 wire pulseaudio[7430]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  4 15:55:25 wire pulseaudio[7430]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  4 15:55:25 wire x-session-manager[7307]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Dec  4 15:55:35 wire x-session-manager[7307]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Dec  4 15:55:45 wire x-session-manager[7307]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Dec  4 15:55:45 wire pulseaudio[7430]: module-x11-xsmp.c: X11 session manager not running.
Dec  4 15:55:45 wire pulseaudio[7430]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Dec  4 15:55:54 wire kernel: [ 1476.414554] compiz.real[7533] trap stack segment ip:41024e sp:7fff3f344170 error:0
Dec  4 15:55:55 wire acpid: client connected from 6808[0:0] 
Dec  4 15:55:55 wire bonobo-activation-server (squeeze-7670): could not associate with desktop session: Failed to connect to socket /tmp/dbus-7U8HV8f99O: Connection refused
Dec  4 15:55:55 wire acpid: client connected from 6808[0:0] 
```

**user.log**
```
Dec  4 15:55:25 wire pulseaudio[7428]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  4 15:55:25 wire pulseaudio[7430]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  4 15:55:25 wire pulseaudio[7430]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  4 15:55:45 wire pulseaudio[7430]: module-x11-xsmp.c: X11 session manager not running.
Dec  4 15:55:45 wire pulseaudio[7430]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Dec  4 15:55:55 wire bonobo-activation-server (squeeze-7670): could not associate with desktop session: Failed to connect to socket /tmp/dbus-7U8HV8f99O: Connection refused
```

---

### Post by graysky on 2009-01-01
Wow, it seems as though this is a known issue!

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467)
[https://bugs.launchpad.net/ubuntu/+bug/292376](https://bugs.launchpad.net/ubuntu/+bug/292376)

Here is the solution!

System>Preferences>Sessions - unchecked Windows Manager
Added a new one called 'fusion-icon' what simply has the command: fusion-icon

ctrl+alt+backspace to restart gdm and it's fixed :)

---

