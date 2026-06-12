---
title: "FreeNX problem with logon"
date: 2009-02-25
forum: General Help
---

### Post by mexus on 2009-02-25
I have 2 servers both running Ubuntu Server 8.10 + KDE 4.2 + Lamp,
different hardware.

I have setup FreeNX server and it works on the first one with no problems, 
but on the second one i get: Connection Timeout.

Details:
```

NX> 203 NXSSH running with pid: 8656
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XXX.XXX.XXX.XXX on port: 22
NX> 202 Authenticating user: nx
* * * * * * * * * * * W A R N I N G * * * * * * * * * * * * *
THIS COMPUTER SYSTEM IS RESTRICTED TO AUTHORIZED USERS ONLY.
UNAUTHORIZED ACCESS IS STRICTLY PROHIBITED AND MAY BE

PUNISHABLE UNDER THE COMPUTER FRAUD AND ABUSE ACT OF 1986 OR
OTHER APPLICABLE LAWS. IF NOT AUTHORIZED TO ACCESS THIS SYSTEM,
DISCONNECT NOW. ANY ILLEGAL SERVICES RUN BY USER OR ATTEMPTS
TO TAKE DOWN THIS SERVER OR ITS SERVICES WILL BE REPORED TO
LOCAL LAW ENFORCMENT, AND SAID USER WILL BE PROSECUTED
TO THE FULL EXTEND OF THE LAW. BY CONTINUING, YOU CONSENT
TO YOUR KEYSTROKES AND DATA CONTENT BEING MONITORED.
ALL PERSONS ARE HEREBY NOTIFIED THAT THE USE OF THIS
SYSTEM CONSTITUTES CONSENT TO MONITORING AND AUDITING.

ANYONE USING THIS SYSTEM CONSENTS TO THESE TERMS!


NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: master
NX> 102 Password: 
NX> 103 Welcome to: master user: master
NX> 105 listsession --user="master" --status="suspended,running" --geometry="2304x1024x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'master' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: master
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="1" --mediahelper="esd" --session="master" --type="unix-kde" --geometry="2304x997" --client="linux" --keyboard="pc102/us" --screeninfo="2304x997x24+render" 

NX> 280 Exiting on signal: 15

```


The first one (working one) has monitor connected to it. The second doesn't. Can someone please help?

---

