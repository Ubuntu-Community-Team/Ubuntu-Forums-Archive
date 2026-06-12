---
title: "ubuntu rebboted while i was working why?"
date: 2009-01-20
forum: General Help
---

### Post by unix1adm on 2009-01-20
ubuntu crashed. how do i find out why
I was surfing the net and al of a sudden the laptop IBM r51 just loged me out went down and came back up really fast.

Here is some of the syslog info....

I dont understand what went wrong.


Jan 20 20:07:39 cj454-lt gdmgreeter[7011]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks",
Jan 20 20:07:45 cj454-lt pulseaudio[7131]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 20 20:07:45 cj454-lt pulseaudio[7134]: pid.c: Stale PID file, overwriting.
Jan 20 20:07:45 cj454-lt pulseaudio[7134]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 20 20:07:45 cj454-lt pulseaudio[7134]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 20 20:07:56 cj454-lt x-session-manager[7031]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Jan 20 20:08:06 cj454-lt x-session-manager[7031]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Jan 20 20:08:06 cj454-lt pulseaudio[7134]: module-x11-xsmp.c: X11 session manager not running.
Jan 20 20:08:06 cj454-lt pulseaudio[7134]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 20 20:08:08 cj454-lt anacron[7388]: Anacron 2.3 started on 2009-01-20
Jan 20 20:08:08 cj454-lt anacron[7388]: Normal exit (0 jobs run)
Jan 20 20:09:10 cj454-lt kernel: [ 2866.531552] ppdev0: registered pardevice
Jan 20 20:09:10 cj454-lt kernel: [ 2866.580984] ppdev0: unregistered pardevice
Jan 20 20:09:12 cj454-lt kernel: [ 2868.044627] ppdev0: registered pardevice
Jan 20 20:09:12 cj454-lt hp: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 20 20:09:12 cj454-lt kernel: [ 2868.092689] ppdev0: unregistered pardevice
Jan 20 20:09:13 cj454-lt kernel: [ 2868.791825] ppdev0: registered pardevice
Jan 20 20:09:13 cj454-lt python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 20 20:09:13 cj454-lt kernel: [ 2868.840176] ppdev0: unregistered pardevice
Jan 20 20:17:01 cj454-lt /USR/SBIN/CRON[7571]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)

---

### Post by unix1adm on 2009-01-20
some more info i missed at the top

Jan 20 20:02:06 cj454-lt -- MARK --
[B][U]Jan 20 20:07:35 cj454-lt kernel: [ 2771.019142] compiz.real[5523]: segfault at 2c0 ip 08055c8c sp bfeffa10 error 4 in compiz.real[8048000+34000]
Jan 20 20:07:35 cj454-lt gdm[5049]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jan 20 20:07:35 cj454-lt bonobo-activation-server (cj454-6956): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Yr3jJBLkHg: Connection refused
Jan 20 20:07:36 cj454-lt acpid: client connected from 6996[0:0] [/U][/B]
Jan 20 20:07:36 cj454-lt kernel: [ 2772.533725] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Jan 20 20:07:36 cj454-lt kernel: [ 2772.533784] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Jan 20 20:07:36 cj454-lt kernel: [ 2772.533850] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Jan 20 20:07:37 cj454-lt kernel: [ 2772.758449] [drm] Setting GART location based on new memory map
Jan 20 20:07:37 cj454-lt kernel: [ 2772.758478] [drm] Loading R100 Microcode
Jan 20 20:07:37 cj454-lt kernel: [ 2772.758538] [drm] writeback test succeeded in 2 usecs
Jan 20 20:07:39 cj454-lt gdmgreeter[7011]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Jan 20 20:07:45 cj454-lt pulseaudio[7131]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 20 20:07:45 cj454-lt pulseaudio[7134]: pid.c: Stale PID file, overwriting.
Jan 20 20:07:45 cj454-lt pulseaudio[7134]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 20 20:07:45 cj454-lt pulseaudio[7134]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 20 20:07:56 cj454-lt x-session-manager[7031]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Jan 20 20:08:06 cj454-lt x-session-manager[7031]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jan 20 20:08:06 cj454-lt pulseaudio[7134]: module-x11-xsmp.c: X11 session manager not running.
Jan 20 20:08:06 cj454-lt pulseaudio[7134]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 20 20:08:08 cj454-lt anacron[7388]: Anacron 2.3 started on 2009-01-20
Jan 20 20:08:08 cj454-lt anacron[7388]: Normal exit (0 jobs run)
Jan 20 20:09:10 cj454-lt kernel: [ 2866.531552] ppdev0: registered pardevice
Jan 20 20:09:10 cj454-lt kernel: [ 2866.580984] ppdev0: unregistered pardevice
Jan 20 20:09:12 cj454-lt kernel: [ 2868.044627] ppdev0: registered pardevice
Jan 20 20:09:12 cj454-lt hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 20:09:12 cj454-lt kernel: [ 2868.092689] ppdev0: unregistered pardevice
Jan 20 20:09:13 cj454-lt kernel: [ 2868.791825] ppdev0: registered pardevice
Jan 20 20:09:13 cj454-lt python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 20:09:13 cj454-lt kernel: [ 2868.840176] ppdev0: unregistered pardevice
Jan 20 20:17:01 cj454-lt /USR/SBIN/CRON[7571]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by unix1adm on 2009-01-21
any ideas?

---

