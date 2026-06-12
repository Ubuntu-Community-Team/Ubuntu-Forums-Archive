---
title: "Problem getting FreeNx working - xrdb and freenx-session-launcher"
date: 2008-10-23
forum: Desktop Environments
---

### Post by chrismorris on 2008-10-23
hello,

i am a moderately experienced ubuntu user without a deep technical understanding of how everything hangs togther.

i run ubuntu 8.04 and had NXServer from NoMachine working until i ran into the expiry of the evaluation period.  i uninstalled nxserver and nxnode and installed freenx server using suggestions from eric hammond.  i had to fiddle a few things such as libxcompshad but have managed to get to the pint where i can authenticate but can't establish a session.

the output of the Detail log from the nxclient session is:

NX> 203 NXSSH running with pid: 372
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.150 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: chris
NX> 102 Password: 
NX> 103 Welcome to: ees-ubuntu-desktop user: chris
NX> 105 listsession --user="chris" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'chris' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: chris
NX> 105 startsession  --link="lan" --backingstore="1" --streaming="1" --nodelay="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="ees-local-ak" --type="unix-gnome" --geometry="1280x766" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x766x32+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: ees-ubuntu-desktop-1001-95248880E51299CAC8A30F6AE76B0A14
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: b9103abcecc61a8bd11a322c5edc4013
NX> 702 Proxy IP: 192.168.1.100
NX> 706 Agent cookie: b9103abcecc61a8bd11a322c5edc4013
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 0
NX> 105 /usr/lib/nx/nxserver: line 1370:  9250 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/chris/.nx/F-C-ees-ubuntu-desktop-1001-95248880E51299CAC8A30F6AE76B0A14/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
Can't open /var/lib/nxserver/db/running/sessionId{95248880E51299CAC8A30F6AE76B0A14}: No such file or directory.
NX> 1006 Session status: closed
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{95248880E51299CAC8A30F6AE76B0A14}': No such file or directory
NX> 1001 Bye.
Killed by signal 15.


and the contents of the session file are:


chris@ees-ubuntu-desktop:~$ more /home/chris/.nx/F-C-ees-ubuntu-desktop-1001-95248880E51299CAC8A30F6AE76B0A14/session
xrdb: No such file or directory
xrdb: Can't open display ':1001'
/usr/lib/nx/nxnode: line 333: /usr/bin/nx-session-launcher-suid: No such file or
 directory


i seem to have 2 problems - one with xrdb and inability to open display :1001 and the other with nx-session-launcher-suid.

i haven't the faintest idea of what to do about the xrdb issue but i have tried to find the freenx-session-launcher and install it with no luck.  it is defined as 'deinstall' when i run dpkg and I can't seem to find where to get it from.

can anyone assist?

cheers

chris

---

