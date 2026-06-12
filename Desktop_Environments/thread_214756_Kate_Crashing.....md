---
title: "Kate Crashing...."
date: 2006-07-13
forum: Desktop Environments
---

### Post by zhoux on 2006-07-13
hi, i've recently installed Kubuntu via text-mode cd.  And since I was going to add other repos. i decided to use kate to open the file and edit it manually:

```
sudo kate /etc/apt/sources.list
```

However, instead of opening kate with sources.list showing...I have this very long error:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_Kubuntu__0
and start dcopserver again.
---------------------------------

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
KCrash: Application 'kate' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

drkonqi: cannot connect to X server :0.0

```

I'm not too familiar with KDE, so can anyone clue me in and help me out?

Many thanks in advance.

---

### Post by aysiu on 2006-07-13
```
kdesu kate
``` [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by zhoux on 2006-07-13
awesome, it worked
thanks

though, i'm still getting the first few errors over and over again:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

do you know why is that?

before this clean install, i played around with an old kubuntu "dapper flight" cd.  i had gotten the same errors as above, so i assumed that it'll be solved before final release, but it didn't get solved...why?

---

### Post by aysiu on 2006-07-13
Read the link from the my last post.

---

### Post by zhoux on 2006-07-13
> **aysiu said:**
> Read the link from the my last post.

i already did, but even when i do use kdesu, i still get that error.

then again...maybe i haven't read as thoroughly as i should.;)

---

### Post by Jun-Dai on 2006-07-16
> **zhoux said:**
> awesome, it worked
thanks

though, i'm still getting the first few errors over and over again:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

do you know why is that?

before this clean install, i played around with an old kubuntu "dapper flight" cd.  i had gotten the same errors as above, so i assumed that it'll be solved before final release, but it didn't get solved...why?

Try this: [http://ubuntuforums.org/showthread.php?p=1264009#post1264009](http://ubuntuforums.org/showthread.php?p=1264009#post1264009)

---

