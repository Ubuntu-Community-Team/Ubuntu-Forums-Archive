---
title: "FreeNX after dist-upgrade to 8.04"
date: 2008-04-29
forum: Desktop Environments
---

### Post by infecticide on 2008-04-29
Since i've updated my Kubuntu to 8.04 I haven't been able to use FreeNX, so I decided to reinstall it!

Bad move, I have dependincies issues:



infecticide@avatar:~$ sudo apt-get remove freenx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  freenx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 311kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122889 files and directories currently installed.)
Removing freenx ...
dpkg: error processing freenx (--remove):
 subprocess pre-removal script returned error exit status 127
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 freenx
E: Sub-process /usr/bin/dpkg returned an error code (1)




Little help?  Thanks!

---

### Post by daflame on 2008-04-30
> **infecticide said:**
> Since i've updated my Kubuntu to 8.04 I haven't been able to use FreeNX, so I decided to reinstall it!

Bad move, I have dependincies issues:



infecticide@avatar:~$ sudo apt-get remove freenx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  freenx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 311kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122889 files and directories currently installed.)
Removing freenx ...
dpkg: error processing freenx (--remove):
 subprocess pre-removal script returned error exit status 127
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 freenx
E: Sub-process /usr/bin/dpkg returned an error code (1)




Little help?  Thanks!

First off, where did you get the packages that you installed?  Have you installed any other packages over top?

---

### Post by infecticide on 2008-05-05
From this location:

deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main

And I have installed other apps since installing FreeNX

[EDIT]
I've managed to get everything reinstalled now so that the dpkg configuration was able to proceed properly.

I am now getting the issue below, this was my original issue.  

[NX Client Details Output]
NX> 203 NXSSH running with pid: 19554
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 24.72.xxx.yyy on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.1.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: infecticide
NX> 102 Password: 
NX> 103 Welcome to: avatar user: infecticide
NX> 105 listsession --user="infecticide" --status="suspended,running" --geometry="3360x1050x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'infecticide' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: infecticide
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Avatar" --type="unix-kde" --geometry="3360x976" --client="linux" --keyboard="pc105/us" --screeninfo="3360x976x24+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.1.0)
NX> 700 Session id: avatar-1001-94AE033683F637930144A055B4158F6A
NX> 705 Session display: 1001
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 2afc97fbe64e3b18b7ca1b23858965fa
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 2afc97fbe64e3b18b7ca1b23858965fa
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
/usr/lib/nx/nxserver: line 1368: 19830 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 105 NX> 1006 Session status: running
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/infecticide/.nx/F-C-avatar-1001-94AE033683F637930144A055B4158F6A/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
Can't open /var/lib/nxserver/db/running/sessionId{94AE033683F637930144A055B4158F6A}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{94AE033683F637930144A055B4158F6A}': No such file or directory
NX> 1006 Session status: closed
NX> 1001 Bye.
NX> 280 Exiting on signal: 15



I checked out the session file it mentions:

NXAGENT - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '20071'.
Session: Starting session at 'Mon May  5 21:44:22 2008'.
Info: Proxy running in server mode with pid '20071'.
Info: Waiting for connection from '127.0.0.1' on port '5001'.
Info: Aborting the procedure due to signal '15'.
Error: Aborting session with 'Unable to open display 'nx/nx,options=/home/infecticide/.nx/C-avatar-1001-94AE033683F637930144A055B4158F6A/options:1001''.
Session: Aborting session at 'Mon May  5 21:44:22 2008'.
Session: Session aborted at 'Mon May  5 21:44:22 2008'.



What's gone wrong since I updated to Hardy?  This error was the reason I attempted to uninstall everything and reinstall it.

---

### Post by infecticide on 2008-05-19
There has recently been an upgrade to FreeNX through the datakeylive repository, but the app is still failing with this message in the details on the client:

> 
NX> 203 NXSSH running with pid: 2752
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 24.72.x.x on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
/usr/bin/X11/xauth:  creating new authority file /var/lib/nxserver/home/.Xauthority
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: infecticide
NX> 102 Password: 
NX> 103 Welcome to: avatar user: infecticide
NX> 105 listsession --user="infecticide" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'infecticide' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: infecticide
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Avatar" --type="unix-kde" --geometry="1680x975" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1680x975x32+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: avatar-1001-E7E3CFABC4F158CCC5B779BB81A7A3E6
NX> 705 Session display: 1001
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 55facf0e78f2a6d5662af0e0e4ad4df3
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 55facf0e78f2a6d5662af0e0e4ad4df3
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 1370: 17002 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/infecticide/.nx/F-C-avatar-1001-E7E3CFABC4F158CCC5B779BB81A7A3E6/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 1006 Session status: closed
NX> 1001 Bye.
Can't open /var/lib/nxserver/db/running/sessionId{E7E3CFABC4F158CCC5B779BB81A7A3E6}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{E7E3CFABC4F158CCC5B779BB81A7A3E6}': No such file or directory
NX> 280 Exiting on signal: 15


---

### Post by Eldis on 2008-08-06
I was able to get NX working on 8.04 mythbuntu but essentially the same thing I suppose.

I used the packages that can be found here: [http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

I basically just installed those packages added a user and uncommented more or less the defaults from server and node configs.

My problem is that I can't goto System -> Administration -> Users & Groups + Unlock

The unlock button is grayed out. This is my only problem atm. I would like to do administrative stuff through this but I'm unable to. This + ssh will be my main way of using ubuntu for anything else than a recording backend and watching live tv so it's kind of important :).

Thanks if anyone has any tips on the matter.

---

