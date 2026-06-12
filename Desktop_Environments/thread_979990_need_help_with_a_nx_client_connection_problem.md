---
title: "need help with a nx client connection problem"
date: 2008-11-12
forum: Desktop Environments
---

### Post by ashc on 2008-11-12
hello, i am new to nxclient and I am trying to connect to my ubuntu server but I am having issues with FreeNX any help would be much apreciated...


Here is what the details say on NXClient

it sais authentication complete, then sais connection error?


NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: r16252.ovh.net-1000-54925100B44AAC086A5CE1859BE1BADA
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: bd322a48d61e520202a6cc8fb502b983
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: bd322a48d61e520202a6cc8fb502b983
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/admin/.nx/F-C-r16252.ovh.net-1000-54925100B44AAC086A5CE1859BE1BADA/session". You might also want to try: ssh -X myserver; /usr/bin/nxnode --agent to test the basic functionality. Session log follows:
/usr/bin/nxserver: line 1368: 23542 Terminated sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{54925100B44AAC086A5CE1859BE1BADA}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{54925100B44AAC086A5CE1859BE1BADA}': No such file or directory
NX> 1006 Session status: closed
NX> 1009 Session status: starting
NX> 1009 Session status: starting
NX> 1001 Bye.
NX> 280 Exiting on signal: 15

any ideas, would be much apreciated

---

