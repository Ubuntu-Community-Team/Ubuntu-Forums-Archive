---
title: "NoMachine NX VNC problems"
date: 2009-01-02
forum: General Help
---

### Post by ryanfx on 2009-01-02
Hey everyone.. I'm here going nuts with a few issues.  I can't get NoMachine NX working properly on my one ubuntu server 8.10. (YES I installed gnome on it, NO I don't want to hear why I shouldn't be running a GUI on a server).


I installed the three packages from [http://www.nomachine.com/download-package.php?Prod_Id=359](http://www.nomachine.com/download-package.php?Prod_Id=359)

  # sudo dpkg -i nxclient_3.3.0-3_i386.deb 
  # sudo dpkg -i nxnode_3.3.0-3_i386.deb 
  # sudo dpkg -i nxserver_3.3.0-8_i386.deb

added the line 
```

AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

```

to my /etc/ssh/sshd_config

the problem is whenever I try to connect via the client (from both a ubuntu client and a windows client) I get the following error:

```

NX> 203 NXSSH running with pid: 4424
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.222 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-8 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: steve
NX> 102 Password: ****
NX> 103 Welcome to: esiserver user: steve
NX> 105 Listsession --user="steve" --status="suspended\054running" --geometry="1920x1200x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: steve
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="192.168.1.222" --type="unix-gnome" --geometry="800x600" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="800x600x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: FCCAFE23. To get detailed information about
NX> 595 ERROR: the error search for the string FCCAFE23 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15


```

as well as the following in my /var/log/messages on the server

```

Jan  2 16:33:56 esiserver NXSERVER-3.3.0-8[12394]: User 'steve' logged in from '192.168.1.18'. 'NXLogin::set'
Jan  2 16:33:56 esiserver NXSERVER-3.3.0-8[12394]: Selected node host:localhost with port:22 'main::selectNode'
Jan  2 16:33:56 esiserver NXSERVER-3.3.0-8[12394]: Current selected node: localhost is in status: running  'main::selectNode'
Jan  2 16:33:56 esiserver NXSERVER-3.3.0-8[12394]: Selected session type: unix-gnome allowed in the profile of user: steve 'NXShell::Static'
Jan  2 16:33:57 esiserver NXSERVER-3.3.0-8[12394]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jan  2 16:33:58 esiserver NXSERVER-3.3.0-8[12394]: A valid NX Server public SSH key is missing on the node. '(eval)'
Jan  2 16:34:00 esiserver NXNODE-3.3.0-3[12436]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.3.0-3  (Error id eCA4167) [eCA4167] Logger::log nxnode 2907
Jan  2 16:34:00 esiserver NXNODE-3.3.0-3[12436]: ERROR: NX> 596 ERROR: create session: run commands [eCA4167] Logger::log nxnode 2907
Jan  2 16:34:00 esiserver NXNODE-3.3.0-3[12436]: ERROR: NX> 596 ERROR: execution of last command failed [eCA4167] Logger::log nxnode 2907
Jan  2 16:34:00 esiserver NXNODE-3.3.0-3[12436]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/steve/.nx/C-esiserver-1002-51276C990804A7FFE8F5150405967647/scripts/authority' [eCA4167] Logger::log nxnode 2907

```



any help would be greatly appreciated.  I hope I included enough information to start debugging.. if not please let me know what output you would like to see.

---

### Post by ryanfx on 2009-01-02
fixed the problem... my .Xauthority file had permissions set wrong - it was owned by root!

---

