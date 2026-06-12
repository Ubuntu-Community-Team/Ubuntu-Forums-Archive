---
title: "FreeNX issue"
date: 2008-09-18
forum: Desktop Environments
---

### Post by PeterK2003 on 2008-09-18
I have googled this and I find a lot of people complaining about this but there doesn't seem to be an good solutions.

```
NX> 203 NXSSH running with pid: 3576
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.248 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: XXXUSERXXX
NX> 102 Password: 
NX> 103 Welcome to: grendel user: peterk2003
NX> 105 listsession --user="XXXUSERXXX" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'XXXUSERXXX' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: peterk2003
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="grendel" --type="unix-gnome" --geometry="1280x740" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x740x32+render" 

NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.2.0)
NX> 700 Session id: grendel-1000-8123FB12B2DD06DADEE3EE45D4875C32
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 4d8859201e79b3ece163fbe361a0422f
NX> 702 Proxy IP: 192.168.1.248
NX> 706 Agent cookie: 4d8859201e79b3ece163fbe361a0422f
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/bin/nxserver: line 1531: 12380 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/XXXUSERXXX/.nx/F-C-grendel-1000-8123FB12B2DD06DADEE3EE45D4875C32/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 1009 Session status: starting
Can't open /var/lib/nxserver/db/running/sessionId{8123FB12B2DD06DADEE3EE45D4875C32}: No such file or directory.
NX> 280 Exiting on signal: 15


```

The thing that doesn't make sense is that it worked fine and then just stopped working after i applied some updates.

Anyone have any suggestions?

---

### Post by PeterK2003 on 2008-09-24
anyone?

---

