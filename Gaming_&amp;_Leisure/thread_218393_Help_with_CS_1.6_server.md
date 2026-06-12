---
title: "Help with CS 1.6 server"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by SILENTHILL on 2006-07-18
I tried setting up the hlds but i keep getting this error.

> 
Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash

Console initialized.
scandir failed:/home/brian/hlds/./platform/SAVE
Protocol version 47
Exe version 1.1.2.0/Stdio (valve)
Exe build: 20:06:30 Mar  7 2006 (3421)
STEAM Auth Server
couldn't exec language.cfg
WARNING: UDP_OpenSocket: port: 27015  bind: Address already in use
FATAL ERROR (shutting down): Couldn't allocate dedicated server IP port 27015.
Add "-debug" to the ./hlds_run command line to generate a debug.log to help with solving this problem
Tue Jul 18 10:18:34 MST 2006: Server restart in 10 seconds

I tried other ports but none will work. Also, I'm new to linux.

---

### Post by ToyMachine on 2006-07-18
Mind sending your debug.log?

---

### Post by SILENTHILL on 2006-07-19
here it is.

> 
----------------------------------------------
CRASH: Wed Jul 19 16:36:40 MST 2006
Start Line: ./hlds_i686 -game cstrike +ip 68.228.252.118 +port 2715 +maxplayers 20 +map de_aztec -debug -pidfile hlds.12475.pid
End of crash report
----------------------------------------------
----------------------------------------------
CRASH: Wed Jul 19 16:36:52 MST 2006
Start Line: ./hlds_i686 -game cstrike +ip 68.228.252.118 +port 2715 +maxplayers 20 +map de_aztec -debug -pidfile hlds.12475.pid
End of crash report
----------------------------------------------
----------------------------------------------
CRASH: Wed Jul 19 16:37:03 MST 2006
Start Line: ./hlds_i686 -game cstrike +ip 68.228.252.118 +port 2715 +maxplayers 20 +map de_aztec -debug -pidfile hlds.12475.pid
End of crash report
----------------------------------------------


---

### Post by RoflKopter on 2007-01-16
You are using a router. Put your internal network ip.

---

