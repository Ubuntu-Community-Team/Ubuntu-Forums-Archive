---
title: "FreeNX won't accept connection after reboot"
date: 2009-03-21
forum: General Help
---

### Post by poguemahone on 2009-03-21
I'm running FreeNX server on Xubuntu 8.10.  After I reboot the server, I can't seem to start a freenx session (although it appears to connect okay).  If I log onto the server locally, however, and then try to start a freenx session (from a remote host) then it works again.

Here is the output from my client (No Machine on Win XP):

```
NX> 105 startsession  --virtualdesktop="1" --application="/usr/bin/xfce4-session" --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="alannarose (from home)" --type="unix-application" --geometry="1604x1050" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1604x1050x32+render" 

/usr/bin/nxserver: line 1478: [: too many arguments
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 700 Session id: alannarose-1000-F5603589C23FE1F5637DBCB4B6DB5C7D
NX> 705 Session display: 1000
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: 1dc5f92bc61a15261b3191624c61e286
NX> 702 Proxy IP: 127.0.1.1
NX> 706 Agent cookie: 1dc5f92bc61a15261b3191624c61e286
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
NX> 105 /usr/bin/nxserver: line 1569:  6113 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/justin/.nx/F-C-alannarose-1000-F5603589C23FE1F5637DBCB4B6DB5C7D/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
Can't open /var/lib/nxserver/db/running/sessionId{F5603589C23FE1F5637DBCB4B6DB5C7D}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{F5603589C23FE1F5637DBCB4B6DB5C7D}': No such file or directoryNX> 1006 Session status: closed

NX> 1001 Bye.
NX> 280 Exiting on signal: 15

```

Any ideas?

---

