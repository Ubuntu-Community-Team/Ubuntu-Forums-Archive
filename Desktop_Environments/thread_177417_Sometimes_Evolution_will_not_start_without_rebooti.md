---
title: "Sometimes Evolution will not start without rebooting Ubuntu"
date: 2006-05-16
forum: Desktop Environments
---

### Post by Marc3090 on 2006-05-16
I have an intermittent problem with Evolution.  Sometimes it will not start.  A short description appears on the taskbar saying Starting Evol.. but it goes away and never opens.  If I do a restart on the system it starts back working.  Does anyone know what is going on and how to fix it?

Marc

---

### Post by Nikusan on 2006-05-16
[QUOTE=Marc3090]I have an intermittent problem with Evolution.  Sometimes it will not start.  A short description appears on the taskbar saying Starting Evol.. but it goes away and never opens.  If I do a restart on the system it starts back working.  Does anyone know what is going on and how to fix it?

Marc[/QUOTE]

Launch it from a terminal and post the output here.

---

### Post by Marc3090 on 2006-05-18
[QUOTE=Nikusan]Launch it from a terminal and post the output here.[/QUOTE]

Here is the error message.

mark@lc2000:~$ evolution --offline
adding hook target 'source'

(evolution:21550): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

---

### Post by dcstar on 2006-05-18
[QUOTE=Marc3090]I have an intermittent problem with Evolution.  Sometimes it will not start.  A short description appears on the taskbar saying Starting Evol.. but it goes away and never opens.  If I do a restart on the system it starts back working.  Does anyone know what is going on and how to fix it?

Marc[/QUOTE]
Most likely the evolution-data-server process has crashed, kill it off using Applications-System Tools-System Monitor and then restart the Evolution client.

---

