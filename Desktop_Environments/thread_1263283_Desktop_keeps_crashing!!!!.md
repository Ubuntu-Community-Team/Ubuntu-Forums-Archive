---
title: "Desktop keeps crashing!!!!"
date: 2009-09-10
forum: Desktop Environments
---

### Post by pondo on 2009-09-10
Running 8.10 
2.6.27-11-generic
AMD 64

Desktop randomly crashes and sends me back to the login screen. happens 5-10 times a day... 
here are the syslogs of the last crash. Can anybody shed some light on this. TY!

Sep 10 20:56:50 mom-desktop -- MARK --
Sep 10 21:01:27 mom-desktop kernel: [ 1502.032521] Xorg[6012] general protection ip:7fa57b21f3e6 sp:7fff8342f360 error:0 in ld-2.8.90.so[7fa57b211000+1f000]
Sep 10 21:01:27 mom-desktop kernel: [ 1502.083888] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00000e08 00330021 00000140
Sep 10 21:01:27 mom-desktop kernel: [ 1502.233687] compiz.real[6576]: segfault at 2ae010 ip 000000000041024e sp 00007fff151fe8b0 error 4 in compiz.real[400000+3b000]
Sep 10 21:01:27 mom-desktop gdm[6007]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Sep 10 21:01:27 mom-desktop bonobo-activation-server (mom-7363): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jkgpi8aqut: Connection refused
Sep 10 21:01:28 mom-desktop acpid: client connected from 7422[0:0] 
Sep 10 21:01:29 mom-desktop acpid: client connected from 7422[0:0] 
Sep 10 21:01:30 mom-desktop gdmgreeter[7440]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Sep 10 21:01:32 mom-desktop bonobo-activation-server (mom-7446): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jkgpi8aqut: Connection refused
Sep 10 21:01:34 mom-desktop pulseaudio[7567]: ltdl-bind-now.c: Failed to find original dlopen loader.
Sep 10 21:01:34 mom-desktop pulseaudio[7571]: pid.c: Stale PID file, overwriting.
Sep 10 21:01:34 mom-desktop pulseaudio[7571]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Sep 10 21:01:34 mom-desktop pulseaudio[7571]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Sep 10 21:01:45 mom-desktop x-session-manager[7464]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Sep 10 21:01:55 mom-desktop x-session-manager[7464]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Sep 10 21:01:55 mom-desktop pulseaudio[7571]: module-x11-xsmp.c: X11 session manager not running.
Sep 10 21:01:55 mom-desktop pulseaudio[7571]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Sep 10 21:02:58 mom-desktop kernel: [ 1593.448392] ppdev0: registered pardevice
Sep 10 21:02:58 mom-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Sep 10 21:02:58 mom-desktop kernel: [ 1593.496254] ppdev0: unregistered pardevice
Sep 10 21:02:58 mom-desktop kernel: [ 1593.572602] ppdev0: registered pardevice
Sep 10 21:02:58 mom-desktop kernel: [ 1593.620047] ppdev0: unregistered pardevice
Sep 10 21:02:59 mom-desktop kernel: [ 1594.683204] ppdev0: registered pardevice
Sep 10 21:02:59 mom-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Sep 10 21:02:59 mom-desktop kernel: [ 1594.732378] ppdev0: unregistered pardevice

---

### Post by earthpigg on 2009-09-10
hi,

this is the first line that tells us something:

> Sep 10 21:01:27 mom-desktop kernel: [ 1502.233687] compiz.real[6576]: segfault at 2ae010 ip 000000000041024e sp 00007fff151fe8b0 error 4 in compiz.real[400000+3b000]

looks like compiz.

to confirm, please disable all desktop effects for a day and see if it continues to happen. (set desktop effects to ***none***)

explain to your mom that this is only temporary, to confirm that it is indeed the problem. :D

but a segfault could ***also*** be bad memory... hence, the need to confirm that its a compiz issue and not hardware failure.

you could also look at another 3 or 4 logs from the issue and see if there is any pattern to them. ie: is it ***always*** compiz? is it sometimes firefox or something else?

---

### Post by pondo on 2009-09-10
I ran all the latest updates and removed Compiz completely. Loaded the Nvidia 180 proprietary driver. 

Crashed twice since. Both time while in firefox. 

My Wife (mom) thanks you.... ;-)

Latest crash syslog...

 Sep 10 22:02:03 mom-desktop kernel: [  135.180072] ppdev0: unregistered pardevice
Sep 10 22:02:04 mom-desktop kernel: [  136.347299] ppdev0: registered pardevice
Sep 10 22:02:04 mom-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Sep 10 22:02:04 mom-desktop kernel: [  136.396745] ppdev0: unregistered pardevice
Sep 10 22:04:42 mom-desktop ntpd[5735]: synchronized to 91.189.94.4, stratum 2
Sep 10 22:04:42 mom-desktop ntpd[5735]: kernel time sync status change 0001
Sep 10 22:10:05 mom-desktop kernel: [  617.923670] Xorg[5435] general protection ip:7f9f97abf406 sp:7fff9fccfb60 error:0 in ld-2.8.90.so[7f9f97ab1000+1f000]
Sep 10 22:10:06 mom-desktop kernel: [  618.138781] compiz.real[6006] trap stack segment ip:41023f sp:7fff4042c890 error:0
Sep 10 22:10:06 mom-desktop gdm[5431]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Sep 10 22:10:06 mom-desktop kernel: [  618.447081] npviewer.bin[6163]: segfault at f565d044 ip 00000000f79029f0 sp 00000000ffdb3844 error 4 in libpthread-2.8.90.so[f78fb000+15000]
Sep 10 22:10:06 mom-desktop bonobo-activation-server (mom-6368): could not associate with desktop session: Failed to connect to socket /tmp/dbus-q5DQZAkHha: Connection refused
Sep 10 22:10:07 mom-desktop acpid: client 5435[0:0] has disconnected 
Sep 10 22:10:07 mom-desktop acpid: client 5435[0:0] has disconnected 
Sep 10 22:10:07 mom-desktop acpid: client connected from 6428[0:0] 
Sep 10 22:10:08 mom-desktop acpid: client connected from 6428[0:0] 
Sep 10 22:10:09 mom-desktop gdmgreeter[6446]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Sep 10 22:10:11 mom-desktop bonobo-activation-server (mom-6452): could not associate with desktop session: Failed to connect to socket /tmp/dbus-q5DQZAkHha: Connection refused
Sep 10 22:10:13 mom-desktop pulseaudio[6569]: ltdl-bind-now.c: Failed to find original dlopen loader.
Sep 10 22:10:13 mom-desktop pulseaudio[6573]: pid.c: Stale PID file, overwriting.
Sep 10 22:10:13 mom-desktop pulseaudio[6573]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Sep 10 22:10:13 mom-desktop pulseaudio[6573]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Sep 10 22:10:25 mom-desktop x-session-manager[6470]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Sep 10 22:10:35 mom-desktop x-session-manager[6470]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Sep 10 22:10:35 mom-desktop pulseaudio[6573]: module-x11-xsmp.c: X11 session manager not running.
Sep 10 22:10:35 mom-desktop pulseaudio[6573]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by pondo on 2009-09-10
and again... this one is interesting....syslog  

Sep 10 22:10:35 mom-desktop pulseaudio[6573]: module-x11-xsmp.c: X11 session manager not running.
Sep 10 22:10:35 mom-desktop pulseaudio[6573]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Sep 10 22:17:01 mom-desktop /USR/SBIN/CRON[6885]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 10 22:25:50 mom-desktop kernel: [ 1562.258390] NVRM: Xid (0002:00): 6, PE0001 
Sep 10 22:25:50 mom-desktop kernel: [ 1562.738835] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
Sep 10 22:25:51 mom-desktop kernel: [ 1563.261571] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
Sep 10 22:25:51 mom-desktop kernel: [ 1563.765318] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
Sep 10 22:25:52 mom-desktop kernel: [ 1564.246429] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
Sep 10 22:25:52 mom-desktop kernel: [ 1564.749564] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
Sep 10 22:25:53 mom-desktop kernel: [ 1565.272647] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
Sep 10 22:25:53 mom-desktop kernel: [ 1565.758162] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040


Thanks you gents for helping out. I sure hope its just RAM....

---

### Post by earthpigg on 2009-09-10
no segfault in the last one?

---

### Post by pondo on 2009-09-11
I'm in way over my head here...

Is there anything else I can post that will help identify the issue?

Your guidance is appreciated...

TY

---

### Post by earthpigg on 2009-09-11
no one that i know can look at syslogs and decipher what every little bit means.

all i am doing is looking for patterns and google searching them.



maybe you could help: is there any pattern to what _*you*_ are doing on the computer when this happens? watching youtube with firefox, etc?

---

### Post by pondo on 2009-09-14
Followed your advice and started Googling the Syslog entries... Learned a lot. Found I hadn't fully removed Compiz. Set Visual effects to none. turned off the screensaver. Found that I may have an NVIDIA proprietary driver issue, or a flash plugin issue. After all this, the seems to have stablized... but been fully resolved. I can now surf the web without the desktop crashing and sending me back to the login screen and I noticed my processor utilization is down about 40% when watching streaming video. I can almost watch a full show on fancast before a crash, where it would crash in just a few minutes before the changes. The wife is back in town today, so the real test starts now. If the system stay stable while she does whatever she does on her computer during the day... the fire is out. I would still like to try to stablize this once and for all. 
Thank you for all your help so far... I'll update again in a couple of days...

Mike

---

### Post by krazyd on 2009-09-14
Hi pondo. Your problem is the proprietary nvidia driver, which is known to be buggy. Unfortunately, because the code is not open source, there is little that anyone outside of nvidia can do. 

You can either update your driver to the latest version from the nvidia website, or ask around on [http://nvnews.net](http://nvnews.net) about your error. These are the relevant lines:

> NVRM: Xid (0002:00) ...

---

### Post by pondo on 2009-10-13
I unloaded the Nvidia drivers and... what do you know... the desktop is now rock solid again.

All, thank you for your assistance. the forums are a terrific asset to us noobs.  

Case closed.

---

### Post by Brimfulof2 on 2011-02-17
I was having the same problem. After reading this thread I checked the nVidia drivers (System > Administration > Additional Drivers) and found that I wasn't actually using them, so updated to the most recent and (so far) seems to have solved the problem.

Thanks for the pointers.

---

