---
title: "FreeNX - Server not installed error"
date: 2006-09-19
forum: Desktop Environments
---

### Post by bolerodan on 2006-09-19
Hey guys, i installed FreeNX and im still trying to get this to work.  I keep thinking okay.. follow the guide(s) exactly and it iwll work.... wrong. Anyways i set up a test user account.  Im using the nomachine-key for as im not worried about security.  However everytime i try to connect, i always get this error.  It authenticates, seems to connect fine, then cuts out telling me the server is not installed or the NX servie is disabled.  I have No idea how to fix this, and i have searched all over the net, finding no solution.  Any ideas?

NX> 203 NXSSH running with pid: 6747
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.0.101 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: test
NX> 102 Password: 
NX> 103 Welcome to: Boleros-Desktop user: test
NX> 105 listsession --user="test" --status="suspended,running" --geometry="1680x1050x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'test' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: test
NX> 105 startsession --session="192.168.0.101" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="adsl" --kbtype="pc102/us" --nodelay="1" --backingstore="when_requested" --geometry="800x600+440+195" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="800x600x24+render" 

Permission denied (publickey,password).
Killed by signal 15.

---

