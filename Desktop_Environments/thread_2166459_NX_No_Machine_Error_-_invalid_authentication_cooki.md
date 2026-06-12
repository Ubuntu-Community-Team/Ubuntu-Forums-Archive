---
title: "NX No Machine Error - invalid authentication cookie"
date: 2013-08-09
forum: Desktop Environments
---

### Post by sopel1000 on 2013-08-09
Hi,

I have a dedicated server with NX NoMachine installed. I've configured it once and it has been working for over a year without a single problem. During that time the server was updated and restarted several times, but the NXSERVER has never failed me... until now. It just stopped working... I read all the forums regarding this problem, but nothing has helped. I uninstalled it and installed it again, I changed ssh keys, I fixed some symbolic links (there were some problems in lib directory), but today I ran out of ideas what to change in order to get it working again... Please help! Any hints will be much appreciated!

On client:

```
Info: Display running with pid '9372' and handler '0x43051c'.

NXPROXY - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '10800'.
Session: Starting session at 'Fri Aug  9 18:25:42 2013'.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Fri Aug  9 18:25:47 2013'.
Session: Session terminated at 'Fri Aug  9 18:25:47 2013'.
```

```
"The remote proxy closed the connection while negotiating the session. This may be due to the wrong authentication credentials passed to the server"
```

Log on server /var/log/messages
```

Aug  9 18:25:32 HOSTNAME NXSERVER-3.5.0-11[29558]: User 'XXXX' logged in from 'IP'. 'NXLogin::set'
Aug  9 18:25:34 HOSTNAME NXSERVER-3.5.0-11[29558]: Selected node host:localhost with port:SSHPORT 'main::selectNode'
Aug  9 18:25:34 HOSTNAME NXSERVER-3.5.0-11[29558]: Current selected node: localhost is in status: running  'main::selectNode'
Aug  9 18:25:34 HOSTNAME NXSERVER-3.5.0-11[29558]: Selected session type: unix-kde allowed in the profile of user: XXXX 'NXShell::Static'
Aug  9 18:25:37 HOSTNAME NXSERVER-3.5.0-11[29558]: Session 'D38ACA7C70BB265AC2851A34DC19DEFE' started by user 'XXXX'. 'NXShell::handler_session_start'
Aug  9 18:25:37 HOSTNAME NXNODE-3.5.0-9[29745]: Using port '2008' on node 'HOSTNAME' for session 'unix-kde'. Logger::log nxnode 6243
Aug  9 18:25:37 HOSTNAME NXNODE-3.5.0-9[29745]: Using host from available host list: 'SRV_IP'. Logger::log nxnode 6244
Aug  9 18:25:38 HOSTNAME NXSERVER-3.5.0-11[29558]: User 'XXXX' from 'IP' logged out. 'NXLogin::reset'
Aug  9 18:26:27 HOSTNAME NXNODE-3.5.0-9[29745]: ERROR: run command: process: 29769 finished with: 1 Logger::log nxnode 3907
Aug  9 18:26:28 HOSTNAME NXNODE-3.5.0-9[29773]: ERROR: Error when monitoring session: Unexpected termination of nxagent 'NXSessionMonitor::__setSessionStatus'
Aug  9 18:26:28 HOSTNAME NXNODE-3.5.0-9[29773]: Directory '/home/XXXX/.nx/C-HOSTNAME-2008-D38ACA7C70BB265AC2851A34DC19DEFE' renamed into '/home/XXXX/.nx/F-C-HOSTNAME-2008-D38ACA7C70BB265AC2851A34DC19DEFE' for further investigation Logger::log nxnode 6432
Aug  9 18:26:29 HOSTNAME NXNODE-3.5.0-9[29745]: Session 'unix-kde' on port '2008' failed. Logger::log nxnode 6513
Aug  9 18:26:35 HOSTNAME NXSERVER-3.5.0-11[29770]: ERROR: NXNodeExec: Cannot kill nxssh process: No such process 'NXNodeExec::exec'
Aug  9 18:26:35 HOSTNAME NXSERVER-3.5.0-11[29770]: User 'XXXX' from 'IP' logged out. 'NXLogin::reset'

```

```
Loop: WARNING! Refusing connection from 'NXSERVIP' on port '6008'.
Loop: PANIC! Connection with remote host '127.0.0.1' could not be established.
```

---

### Post by sopel1000 on 2013-09-16
As usual, no reply and no help on this forum. For the record: I have not resolved this issue, the system had to be reinstalled. 

Unfortunately now I am having the same problem on another machine... >.<

---

