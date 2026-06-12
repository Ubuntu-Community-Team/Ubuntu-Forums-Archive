---
title: "Window managers all crash -- After upgrading FreeNX + ssh"
date: 2008-12-01
forum: Desktop Environments
---

### Post by yohansb on 2008-12-01
Hi ppl,

The window managers on my computer aren't working properly any more after upgrading ssh + freenx. Actually I am having a range of issues at the moment so this is getting a bit complicated. Can anyone give some hints as to why FreeNX and XDMCP are not loading the window manager correctly? I am not able to find hints in the error logs, perhaps I am looking in the wrong log files?.

**== summary ==**
* Window managers (gnome,kde,etc) all worked before upgrading freenx + ssh (SSH still works fine)
* FreenNX connects, authenticates, then window manager seems to crash. Why??
  .. whilst writing this up and fiddling I found a way to get FreeNX to work. (I will explain below, see: freeNX : partial fix.. in next message)
* XDMCP brings up the greeting window. After logging in the window manager crashes and I am brought back to kdm_greet  (gnome, kde, twm, etc all crash). Why does it crash?
More fiddling today and I can get an XDMCP to bring up an xterm.. from the xterm I can bring up gnome by running gnome-session
* Window managers work when run locally (when sitting at the computer gnome/etc works, but remote connections are failing (via freenx / xdmcp)
* I am running Ubuntu gutsy (7.10), freenx 0.7.3, nxagent 3.2.0-2-10-0, nxlibs 3.2.0-2-10-0

Now comes the detailed stuff.. hope you guys don't mind a mile of text!



**--== XDMCP ==----------------------------------------------**
Connecting via XDMCP brings up kdm_greet OK, but when I log in I get a grey screen for a few seconds (black and white pixels dithered) and then straight back to the log in screen! Same result for all the available window managers, even for TWM! What the *#$%?!

OK, so I change my settings in XMing to run xterm instead of connecting to the XDMCP default. It works! Well I get an xterm.. and I can run startkde or gnome-session from there! What gives?

/var/log/syslog says:
Dec  2 11:53:54 my-server-name kdm[....]: Unknown session exit code 0 (sig 11) from manager process

No other new log messages except for the ACPI log spam that has already been mentioned, ie "ACPI: Unable to turn cooling device [c1965438] 'on'"

/var/crash/ has a new file : _usr_bin_kdm.0.crash .. but what do I do I make of that? Why does it crash when run from the kde-greeter, and yet work ok from xterm when I run startkde.

---

### Post by yohansb on 2008-12-01
**--== freeNX ==----------------------------------------------**
If I connect via FreeNX to my linux computer .. it connects and is authorised just fine, but just as it tries to load the window manager - everything falls apart. NX briefly shows the window where the KDE / Gnome would load but then it closes after a second.

**--== freeNX : log from PC ==--**
The NoMachine Client reports the following : 
	"Session myservername failed"
The detail box provides the following log:
_** start log..**_
Info: Display running with pid '6852' and handler '0x390c80'.

NXPROXY - Version 3.3.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '6440'.
Session: Starting session at 'Tue Dec  2 09:56:23 2008'.
Warning: Connected to remote version 3.2.0 with local version 3.3.0.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Tue Dec  2 09:56:23 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Tue Dec  2 09:56:24 2008'.
Session: Session terminated at 'Tue Dec  2 09:56:24 2008'.
_** end log..**_

So the session terminated but no helpful info is provided about why the session died.
Not sure of what to make of the warnings in that log:
Warning: Connected to remote version 3.2.0 with local version 3.3.0.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.


**--== freeNX : log from ubuntu ==--**

Looking in /var/log/* I can't see anything helpful

/var/log/syslog is jam full of :
"Dec  2 10:15:49 servername kernel: [123.123] ACPI: Unable to turn cooling device [c1965438] 'on'"
This message is logged every 6 seconds 24*7.. ~14400 copies of the same message a day is really silly.. and annoying. I'll just call that log spam ;)

/var/log/Xorg.0.log -- surprisingly there isn't any new message there.

/var/crash/ has no new files.. although there are recent crashes for yelp, kdm and freenx from previous attempts that were over an hour ago.

/var/log/nxserver.log says ..
_** start log..**_
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: myusername
NX> 102 Password: 
NX> 103 Welcome to: my-server-name user: myusername
NX> 105 listsession --user="myusername" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'myusername' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: myusername
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="32M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="my-server-name" --type="unix-gnome" --geometry="1280x960" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x960x32+render" 

Info: Using /etc/nxserver/nxacl to change session parameters or deny session.
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.2.0)
NX> 700 Session id: my-server-name-1001-[...]
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: [...]
NX> 702 Proxy IP: my_ip_address
NX> 706 Agent cookie: [...]
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
Info: Closing connection to slave with pid 14496.
1001 Bye.
NX> 1006 Session status: closed
NX> 1001 Bye.
Info: Closing connection to slave with pid 14496.
_** end log..**_


**-- freeNX : partial fix? found a way to get it working --**
Just whilst writing this I found that by changing the custom settings I was able to get it to work. But.. why? Here is what I did, perhaps it will help some other poor sod who gets stuck:

	* NX Client >> Configure... >> general tab >> desktop
	* change desktop settings to unix, custom. Click settings..
	* click 'run the following command' and enter 'gnome-session' or 'startkde'.
	click "new virtual desktop' or else your screen will go bonkers with windows popping up everywhere
	* click OK >> Display : Available Area >> now Save
	* now login and connect

Doesn't really make sense as /etc/nxserver/node.conf has the right startup commands, ie:
	COMMAND_START_GNOME=gnome-session
	COMMAND_START_KDE=startkde

/var/log/nxserver.log says ..
_** start log..**_
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: myusername
NX> 102 Password: 
NX> 103 Welcome to: myservername user: myusername
NX> 105 listsession --user="myusername" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-application"
NX> 127 Sessions list of user 'myusername' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: myusername
NX> 105 startsession  --virtualdesktop="1" --application="gnome-session" --link="lan" --backingstore="1" --encryption="1" --cache="32M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="myservername" --type="unix-application" --geometry="1280x960" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x960x32+render" 

Info: Using /etc/nxserver/nxacl to change session parameters or deny session.
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.2.0)
NX> 700 Session id: myservername-1001-[...]
NX> 705 Session display: 1001
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: [...]
NX> 702 Proxy IP: my_ip_address
NX> 706 Agent cookie: [...]
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
_** end log..**_

---

### Post by yohansb on 2008-12-09
OK, I suppose my last post was too long. I will simplify my question:

Q: Why do I need to use a custom command in order to get freeNX working?

FreeNX should be running EXACTLY the same command internally as the one I entered (ie. startkde / gnome-session). What is going wrong and how come I can't find any log files with error messages? Have I missed some other important log file? 

[Thinking out loud] I am pretty sure that I checked ~/.nx .. maybe I should check that more thoroughly.. hmmmmmm..... ?

---

### Post by IsmailBhai on 2009-06-29
any luck? I've been having this problem now

---

### Post by sasa.tomic on 2010-03-05
what solved exactly the same problem in my case was creating a file:
```

/etc/nxserver/node.conf.d/99_ubuntu_bootstrap_override.conf

```

with the following contents:
```

BOOTSTRAP_X_SESSION="0"

```

good luck!

---

