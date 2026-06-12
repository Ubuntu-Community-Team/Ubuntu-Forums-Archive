---
title: "Help with CSS Server"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by chr3681 on 2007-06-02
When I try to start my server for CounterStrike Source on Feisty I keep getting this error:

```
root@thedudz-desktop:~# cd /home/thedudz/srcds_l/
root@thedudz-desktop:/home/thedudz/srcds_l# ./srcds_run -console -game cstrike +map de_duest +ip 192.168.1.105 +maxplayers 16 -autoupdate
Auto detecting CPU
Using AMD Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version …
Updating Installation
Checking/Installing ‘Counter-Strike Source Shared Content’ version 61

Checking/Installing ‘Base Source Shared Models’ version 4

Checking/Installing ‘Base Source Shared Sounds’ version 4

Checking/Installing ‘Base Source Shared Materials’ version 8

Checking/Installing ‘Source Dedicated Server Linux’ version 75

HLDS installation up to date
Illegal instruction (core dumped)
Add “-debug” to the ./srcds_run command line to generate a debug.log to help with solving this problem
Fri Jun 1 15:37:15 EDT 2007: Server restart in 10 seconds
```

Thanks in advance for your help!

---

### Post by Moustacha on 2007-06-02
does your cpu have SSE? Steam server needs SSE to run, so older Athlons/Durons won't be able to run it as they don't have SSE.

---

### Post by chr3681 on 2007-06-03
i think that may be it. guess i'll have to work on getting it up on a different comp. thanks for the info

---

### Post by gvoima on 2007-06-03
Well, try to create the debug log as the log says. And check /proc/cpuinfo about the SSE.

---

### Post by Rocket2DMn on 2007-06-04
I don't think"de_duest" a map, even in CS:S.  try "+map de_dust" instead :)
I suggest you use a secure server as well (unless this is done automatically with source?).
You probably also need command line options like maxplayers.
The following is my cs1.6 bootup line for your reference:

> ./hlds_run -game cstrike +map de_rats +maxplayers 17 +port 27015 +servercfgfile 
rats.cfg +mapcyclefile ratscycle.txt sport 29015 -autoupdate

You should probably at least have: game, map, maxplayers, port, and autoupdate

---

