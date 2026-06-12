---
title: "Nomachine Fails To Start Session"
date: 2013-02-20
forum: Desktop Environments
---

### Post by user2037 on 2013-02-20
I had this working after much fiddling from a Win7 client, but now I can cannot reproduce success with Xubuntu 12.10 (client) to Xubuntu 12.04 (server).

Tried using Unix, XDM but to no avail. Apparently Xubuntu 12.04 is using Lightdm for the welcome screen. Installing XDM did not help.

Ideas?

---

### Post by MrKaliman on 2013-02-20
Any error messages?

---

### Post by user2037 on 2013-02-20
Logs:
```

Feb 20 12:28:46 myuser-computer NXSERVER-3.5.0-9[4512]: User 'myuser' logged in from '192.168.0.100'. 'NXLogin::set'
Feb 20 12:28:47 myuser-computer NXSERVER-3.5.0-9[4512]: Selected node host:localhost with port:22 'main::selectNode'
Feb 20 12:28:47 myuser-computer NXSERVER-3.5.0-9[4512]: Current selected node: localhost is in status: running  'main::selectNode'
Feb 20 12:28:47 myuser-computer NXSERVER-3.5.0-9[4512]: Selected session type: unix-xdm allowed in the profile of user: myuser 'NXShell::Static'
Feb 20 12:28:50 myuser-computer NXNODE-3.5.0-7[4903]: Using port '1039' on node 'myuser-computer' for session 'unix-xdm'. Logger::log nxnode 6243
Feb 20 12:28:50 myuser-computer NXNODE-3.5.0-7[4903]: Using host from available host list: 'localhost'. Logger::log nxnode 6244
Feb 20 12:28:50 myuser-computer NXSERVER-3.5.0-9[4512]: Session 'D8900BC341409245FB3ED4881120175F' started by user 'myuser'. 'NXShell::handler_session_start'
Feb 20 12:28:50 myuser-computer NXSERVER-3.5.0-9[4512]: User 'myuser' from '192.168.0.100' logged out. 'NXLogin::reset'
Feb 20 12:29:29 myuser-computer NXNODE-3.5.0-7[4903]: Session 'unix-xdm' on port '1039' closed. Logger::log nxnode 6530
Feb 20 12:29:31 myuser-computer NXSERVER-3.5.0-9[4929]: session sessionId:D8900BC341409245FB3ED4881120175F finished 'NXShell::handler_session_start'
Feb 20 12:29:31 myuser-computer NXSERVER-3.5.0-9[4929]: Session 'D8900BC341409245FB3ED4881120175F' closed by user 'myuser'. 'NXShell::Static'
Feb 20 12:33:19 myuser-computer NXSERVER-3.5.0-9[5794]: User 'myuser' logged in from '192.168.0.100'. 'NXLogin::set'
Feb 20 12:33:19 myuser-computer NXSERVER-3.5.0-9[5794]: Selected node host:localhost with port:22 'main::selectNode'
Feb 20 12:33:19 myuser-computer NXSERVER-3.5.0-9[5794]: Current selected node: localhost is in status: running  'main::selectNode'
Feb 20 12:33:19 myuser-computer NXSERVER-3.5.0-9[5794]: Selected session type: unix-xdm allowed in the profile of user: myuser 'NXShell::Static'
Feb 20 12:33:22 myuser-computer NXNODE-3.5.0-7[6185]: Using port '1040' on node 'myuser-computer' for session 'unix-xdm'. Logger::log nxnode 6243
Feb 20 12:33:22 myuser-computer NXNODE-3.5.0-7[6185]: Using host from available host list: 'localhost'. Logger::log nxnode 6244
Feb 20 12:33:22 myuser-computer NXSERVER-3.5.0-9[5794]: Session 'CB6A26E2CB8448BAFAA58E40EC139485' started by user 'myuser'. 'NXShell::handler_session_start'
Feb 20 12:33:22 myuser-computer NXSERVER-3.5.0-9[5794]: User 'myuser' from '192.168.0.100' logged out. 'NXLogin::reset'
Feb 20 12:33:53 myuser-computer NXNODE-3.5.0-7[6185]: Session 'unix-xdm' on port '1040' closed. Logger::log nxnode 6530
Feb 20 12:33:55 myuser-computer NXSERVER-3.5.0-9[6211]: session sessionId:CB6A26E2CB8448BAFAA58E40EC139485 finished 'NXShell::handler_session_start'
Feb 20 12:33:55 myuser-computer NXSERVER-3.5.0-9[6211]: Session 'CB6A26E2CB8448BAFAA58E40EC139485' closed by user 'myuser'. 'NXShell::Static'
Feb 20 12:35:10 myuser-computer NXSERVER-3.5.0-9[6422]: User 'myuser' logged in from '192.168.0.100'. 'NXLogin::set'
Feb 20 12:35:10 myuser-computer NXSERVER-3.5.0-9[6422]: Selected node host:localhost with port:22 'main::selectNode'
Feb 20 12:35:10 myuser-computer NXSERVER-3.5.0-9[6422]: Current selected node: localhost is in status: running  'main::selectNode'
Feb 20 12:35:10 myuser-computer NXSERVER-3.5.0-9[6422]: Selected session type: unix-application allowed in the profile of user: myuser 'NXShell::Static'
Feb 20 12:35:13 myuser-computer NXSERVER-3.5.0-9[6422]: Session 'F80AA17AE22F9CA1F1CD4C56D22899C5' started by user 'myuser'. 'NXShell::handler_session_start'
Feb 20 12:35:13 myuser-computer NXSERVER-3.5.0-9[6422]: User 'myuser' from '192.168.0.100' logged out. 'NXLogin::reset'
Feb 20 12:35:14 myuser-computer NXNODE-3.5.0-7[6814]: Using port '1041' on node 'myuser-computer' for session 'unix-application'. Logger::log nxnode 6243
Feb 20 12:35:14 myuser-computer NXNODE-3.5.0-7[6814]: Using host from available host list: 'localhost'. Logger::log nxnode 6244
Feb 20 12:35:17 myuser-computer NXNODE-3.5.0-7[6842]: ERROR: run command: process: 6852 finished with: 127 Logger::log nxnode 3907
Feb 20 12:35:17 myuser-computer NXNODE-3.5.0-7[6842]: ERROR: session monitor: process connections: failed execution of command '/usr/sbin/lsof -w -b -Ff -p 6838 -a -U': output was: open3: exec of /usr/sbin/lsof -w -b -Ff -p 6838 -a -U failed: No such file or directory at nxnode.pl line 3588\n, exit value: 255 Logger::log nxnode 11318
Feb 20 12:35:17 myuser-computer NXNODE-3.5.0-7[6842]: ERROR: session monitor: connection number cannot be less than 2: shutting down session Logger::log nxnode 8899
Feb 20 12:35:20 myuser-computer NXNODE-3.5.0-7[6814]: Session 'unix-application' on port '1041' closed. Logger::log nxnode 6530
Feb 20 12:35:22 myuser-computer NXSERVER-3.5.0-9[6841]: session sessionId:F80AA17AE22F9CA1F1CD4C56D22899C5 finished 'NXShell::handler_session_start'
Feb 20 12:35:22 myuser-computer NXSERVER-3.5.0-9[6841]: Session 'F80AA17AE22F9CA1F1CD4C56D22899C5' closed by user 'myuser'. 'NXShell::Static'

```

---

