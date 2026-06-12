---
title: "Problems with Freenx - Session startup failed - Please help."
date: 2006-06-19
forum: Desktop Environments
---

### Post by drdnl on 2006-06-19
Basically the first problem that I haven't been able to fix with the aid of google and restart/reinstalling everything (former windows user :)).

I'm trying to get freenx working on my xgl/compiz enabled box (but it doesnt work when I switch that off) using nvidia drivers.

I followed this [tutorial]("https://help.ubuntu.com/community/FreeNX")

and got it to work once, with the below error showing up depending on what pc I was on, windows or linux. Now however I only get the error below, is there anyone out there that can figure out what's wrong? I've switched nearly everything over from windows but I'd like to be able to login remotely....

Regards,
D

```
NX> 203 NXSSH running with pid: 1032
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 10.0.0.150 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: daniel
NX> 102 Password: 
NX> 103 Welcome to: ubuntu user: daniel
NX> 105 listsession --user="daniel" --status="suspended,running" --geometry="1024x768x16+render" --type="unix-gnome"
NX> 127 Sessions list of user 'daniel' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: daniel
NX> 105 startsession --session="D2" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="wan" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1024x740x16+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: ubuntu-1000-4D8C032A9F5AB3236CECB513AC50B7DE
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: c2d17bd37fb738ea5e47f223d77efe08
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: c2d17bd37fb738ea5e47f223d77efe08
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 891: 21928 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: NXAGENT: Fatal IO error on display "nx/nx,options=/home/daniel/.nx/C-ubuntu-1000-4D8C032A9F5AB3236CECB513AC50B7DE/options:1000".
NX> 1001 Bye.
Killed by signal 15.
```

---

### Post by drdnl on 2006-06-20
Well, it seems to be working now, though I'm not entirely sure what happened... I've rebooted multiple times and have logged in multiple times and all seems to be ok. Thank you anyway if you checked what was wrong,

-D

---

