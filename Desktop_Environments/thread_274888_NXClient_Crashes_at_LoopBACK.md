---
title: "NXClient Crashes at LoopBACK"
date: 2006-10-10
forum: Desktop Environments
---

### Post by Jaygo333 on 2006-10-10
My NXClient crashes when i try to open a loopback to my onw machine during Authentication.
I do know Port 22 is open since I can NX to another PC but not my own.
Here are the details of my NX Client  when it  crashes.

NX> 203 NXSSH running with pid: 8925
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: *.*.*.* on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: jaygo333
NX> 102 Password: 
NX> 103 Welcome to: dapper user: jaygo333
NX> 105 listsession --user="jaygo333" --status="suspended,running" --geometry="1280x1024x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'jaygo333' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: jaygo333
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="1" --mediahelper="esd" --session="Jaygo333" --type="unix-gnome" --cookie="******" --geometry="1280x970" --kbtype="pc102/us" --screeninfo="1280x970x24+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: dapper-1000-39DAAF4ED21E18E44C29AE7B85BC14E1
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: cfa8a80a3f428aacfc6e609cdf5befcc
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 2a211a429cf7055018e03819094a8c85
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 880:  9042 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.

HELP PLZ.
I'm just testing so that I can connect at other PC's

---

### Post by drdnl on 2006-11-08
I have the exact same error when running Gnome/nxserver and nxclient, it logs in, authenticates and then just dies. For me the solution is to run NO p2p software. As long as azureus and amule are not running it works fine,

does this work for anyone?

---

### Post by raju.mailinglists on 2006-11-20
On a debian Etch machine, I have similar errors. I dont think the problem is related to P2P software. Any ideas on how to get nxclient to work? My errors are

NX> 203 NXSSH running with pid: 8343
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 128.253.28.128 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: rajulocal
NX> 102 Password: 
NX> 103 Welcome to: kusumanchi user: rajulocal
NX> 105 listsession --user="rajulocal" --status="suspended,running" --geometry="1440x900x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'rajulocal' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: rajulocal
NX> 105 startsession --session="rajulocal@laptopschool" --type="unix-kde" --cache="8M" --images="32M" --cookie="******" --link="adsl" --kbtype="pc102/us" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="1362x900" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1362x900x24+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: kusumanchi-[00m1000-[00m0460E08B7A15521C3EF123A913E30493
NX> 705 Session display: [00m1000
NX> 703 Session type: [00munix-kde
NX> 701 Proxy cookie: 1b867e3cc75eaa1d8d77be962868ab86
NX> 702 Proxy IP: [00m128.253.28.128
NX> 706 Agent cookie: [00m0dbee8d1b29f7f418ccaeb8310a7de55
NX> 704 Session cache: [00munix-kde
NX> 707 SSL tunneling: [00m1
/usr/lib/nx/nxserver: line 891:  8481 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: -geometry
NX> 1001 Bye.
Killed by signal 15

---

