---
title: "[SOLVED] how do i start/enable XDMCP without a Desktop Manager ??? is it pssoble ?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Markkreuzz on 2006-09-27
Hello,
       Firstly the reason i would like to enable XDMCP on my machine is to be able to connect Xming or Cygwin to my Dapper PC. and secondly i have disabled/removed xdm gdm on my system and my system starts up using startx automagically w/out any Desktop Managers, and now i'm thiking that might have been a bad idea removing DMs because i cannot find any howto's or guides to enable XDMCP without a DM :cry: ........... I hope someone could help me on this one or point me to anything useful... or even tell if it is even possible... thanks

---

### Post by fnjordy on 2006-09-27
With GDM you just add the option "--no-console" on the command line.

```

--- /etc/init.d/gdm.orig        2006-09-28 01:14:56.000000000 +0800
+++ /etc/init.d/gdm     2006-09-28 01:17:27.000000000 +0800
@@ -56,7 +56,7 @@
                        /etc/init.d/usplash start
                fi
                log_begin_msg "Starting GNOME Display Manager..."
-               start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
+               start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE --no-console >/dev/null 2>&1 || log_end_msg 1
                log_end_msg 0
        fi
   ;;


```

---

### Post by Markkreuzz on 2006-09-27
:icon_frown:  thanks for your reply, except i don't have GDM installed... would this work if i put it in my /etc/rc.local ???

:-k 
:edited:

i have just reading on an alternative (FreeNX) and that too requires a DM to work properly. i never really tought that DMs are really that important... always tought they were a nuissance....

---

### Post by fnjordy on 2006-09-29
The DM in XDMCP is Display Manager, the same DM as in GDM, so its a bit difficult without one running.

:p

---

### Post by Markkreuzz on 2006-09-30
OoooOOokay that would make it obvious.... Guess its time to accept this hard fact... I'll just gonna use GDM since i have read that XDM is a bit buggy under Debian and derivatives... thanks again for the answer......

---

