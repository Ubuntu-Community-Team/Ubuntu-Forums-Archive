---
title: "Why can I shadow Mint desktops, but not Ubuntu (with Nomachine)"
date: 2013-05-21
forum: Desktop Environments
---

### Post by Cursed Lemon on 2013-05-21
I've been trying to find a solution to this for ages. 

Whenever I try to shadow a Mint desktop using Nomachine (from a Ubuntu system, or a Mint system) I am able to do so easily and effectively. However, whenever I try to shadow a Ubuntu session, I get the following options: 

[IMG]http://i.imgur.com/WTGUcQl.png[/IMG]

Both of which produce the exact same error:

```
NX> 203 NXSSH running with pid: 6348
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.68 on port: 6275
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-23-generic i686)

 * Documentation:  https://help.ubuntu.com/

HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: support
NX> 102 Password: 
NX> 103 Welcome to: colombo user: support
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            B0A639B5850EB99734F2B0885D7A4A64 --------                      Running     X0 (Local)
0       Local            E175675B56EC875B4BD02AF6AA920183 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            B0A639B5850EB99734F2B0885D7A4A64 --------                      Running     X0 (Local)
0       Local            E175675B56EC875B4BD02AF6AA920183 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            B0A639B5850EB99734F2B0885D7A4A64 --------                      Running     X0 (Local)
0       Local            E175675B56EC875B4BD02AF6AA920183 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 listsession --type="shadow"
NX> 127 Sessions list of user '.*' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            B0A639B5850EB99734F2B0885D7A4A64 --------                      Running     X0 (Local)
0       Local            E175675B56EC875B4BD02AF6AA920183 --------                      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: .*
NX> 105 attachsession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="colombo" --type="shadow" --client="linux" --keyboard="pc105/us" --id="E175675B56EC875B4BD02AF6AA920183" --display="0"

NX> 596 Could not find shadowed session E175675B56EC875B4BD02AF6AA920183. Session failed.
NX> 596 Sharing: 
NX> 105 NX> 280 Exiting on signal: 15


```

---

