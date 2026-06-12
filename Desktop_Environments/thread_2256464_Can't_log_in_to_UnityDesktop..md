---
title: "Can't log in to Unity/Desktop."
date: 2014-12-12
forum: Desktop Environments
---

### Post by Azyx on 2014-12-12
Have to make a reboot after upgrade, and now it can not log in to grafical mode/Unity. The monitor whent black and no signal.

I can log in  from another computer via ssh AND i can reach samba shared folders fromanother computer :)

Have Ubuntu 14.04LTS. How to fix? I have  AMD APU/gxf (E450M-M1 pro)

PS. I have run "sudo apt-get update && sudo apt-get upgrade" from ssh.

During startup, I see startup text and there are 2 errorrs (red text), but I have no time to see what it says. After that, the monitor whent black.

---

### Post by Azyx on 2014-12-13
I have tried:

```

Azyx@Blackus:/$ sudo service lightdm stop
lightdm stop/waiting
Azyx@Blackus:/$ sudo X -configure
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running
(EE) 
Fatal server error:
(EE) Cannot establish any listening sockets - Make sure an X server isn't already running(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.

```

PS. "/var/log/Xorg.0.log" have the same info as shown above.


I also have read xsession-errors in my homefolder  nano .xsession-errors and find this:

```
Script for ibus started at run_im.
init: unity-settings-daemon main process ended, respawning
init: gnome-session (Unity) main process (1384) terminated with status 1
init: unity-panel-service main process (1458) terminated with status 1
init: indicator-bluetooth main process (2107) killed by TERM signal
init: indicator-power main process (2131) killed by TERM signal
init: indicator-datetime main process (2153) killed by TERM signal
init: indicator-printers main process (2171) terminated with status 1
init: indicator-session main process (2178) killed by TERM signal
init: unity-settings-daemon main process (13443) terminated with status 1
init: indicator-application main process (2191) killed by TERM signal
init: hud main process (1378) terminated with status 1
init: Disconnected from notified D-Bus bus
```

---

### Post by Azyx on 2014-12-15
UNSOLVED. Had to go back to kernel 3.13.0-34-generic

lot of Error popup, but i work now...

---

### Post by ben147 on 2015-03-07
I dont have a solution but I am curious about process 1384. Maybe this might give you some insight, too. I have two users, the second one I created by copying the first one and making the second one owning the new files. Now I want to delete the first user but it's not possible because process 1384 is still in use by the first user (although I logged out) and so /usr/sbin/userdel" returns error code 8.

---

### Post by Azyx on 2015-03-07
After a few weeks an upgrade came that fix the problem. May have being some problem with propretarian gfx-drivers. Thanx.

---

