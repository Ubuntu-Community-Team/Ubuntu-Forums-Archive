---
title: "/etc/rc.d/ is gone - Cant connect via nx server"
date: 2009-01-23
forum: General Help
---

### Post by Fredrik_b on 2009-01-23
this night after 104 days of uptime my linux server stoped responding to SMB lookup so i tried to restart samba but found out that the rc.d catalog is gone i have rc0.d - rc6.d insted.

A reboot solved the samba issue but I cant connect to the server via NX client / NX server. SSH via putty works

I get this message:

```
NX> 203 NXSSH running with pid: 2636
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.105 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-15 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: ad
NX> 102 Password: ********
NX> 103 Welcome to: server user: ad
NX> 105 Listsession --user="ad" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-application" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: B879889F. To get detailed information about
NX> 595 ERROR: the error search for the string B879889F in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```

using 8.04

---

