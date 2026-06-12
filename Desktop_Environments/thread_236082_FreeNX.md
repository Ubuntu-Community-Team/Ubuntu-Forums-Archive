---
title: "FreeNX"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jwe on 2006-08-14
Hi

I am having problems getting FreeNX to work again after my dapper upgrade. I uninstalled freenx and followed Fisslefink's instructions but still no luck. I have reinstalled it again and am now using the nomachine keys to get it working but I keep getting an error about nxagent. Does anyone have the same problem?
This is the log I get:

NX> 203 NXSSH running with pid: 1772
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.101 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: jaco
NX> 102 Password: 
NX> 103 Welcome to: BIGUBUNTU user: jaco
NX> 105 listsession --user="jaco" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'jaco' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: jaco
NX> 105 startsession  --link="lan" --backingstore="1" --nodelay="1" --cache="8M" --images="32M" --media="0" --session="Ubu" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/gb" --screeninfo="1024x768x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: BIGUBUNTU-1000-2308221B4B37027EED35FEB72C6C1705
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 0c196d0d4cd59fce5c1892c0b38b7785
NX> 702 Proxy IP: 192.168.0.105
NX> 706 Agent cookie: b7294f50a01662fc0ad896b667d36ff8
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 0
/usr/lib/nx/nxserver: line 880:  7094 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.

---

### Post by jwe on 2006-08-14
not to worry. Followed these instructions:
[http://www.ubuntuforums.org/showthread.php?t=204976&highlight=freenx](http://www.ubuntuforums.org/showthread.php?t=204976&highlight=freenx)
works like a charm.

---

### Post by stinerman on 2006-08-15
I have the same problem.

Apparently, the server chokes on any commands from a Windows client (or at least anything v2.0).

Has anyone sucessfully connected to their FreeNX server with a new windows client?

---

