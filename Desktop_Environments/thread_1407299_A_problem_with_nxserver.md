---
title: "A problem with nxserver"
date: 2010-02-15
forum: Desktop Environments
---

### Post by gluk1024 on 2010-02-15
Hello, I'm getting an error while trying to connect remotely to my Kubuntu machine from a Windows client using nomachine's NXClient.

At home I was able to connect to it easily using local network and a Kubuntu client.

I was searching if anyone have the same problem, but there are no posts with the same error

Here is the output of NXClient:
```
NX> 203 NXSSH running with pid: 3756
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 76.133.154.235 on port: 5001
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.4.0-8 - LFE
NX> 105 Hello NXCLIENT - Version 3.4.0
NX> 134 Accepted protocol: 3.4.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: gluk1024
NX> 102 Password: **************
NX> 103 Welcome to: placsin-desktop user: gluk1024
NX> 105 Listsession --user="gluk1024" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-kde" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: gluk1024
NX> 105 Start session with: --link="adsl" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="gluk" --type="unix-kde" --geometry="1274x969" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1274x969x32+render" 
NX> 600 Not enought X resouces to start another session
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```

Could anyone give an advice on how to fix this?

Thanks all :)

---

