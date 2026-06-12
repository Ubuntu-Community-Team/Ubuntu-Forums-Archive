---
title: "FreeNX - Unable to login successfully, error code: 2E7C3711"
date: 2008-12-16
forum: General Help
---

### Post by ecorg911 on 2008-12-16
Hello, Firstly I would like to appologise if this is in the wrong section. I have been trying to get FreeNX setup on my debian server for a while now, although to no avail :(

I have installed and setup nxnode, nxserver, nxclient ( all in the correct order.)

I have setup a use, and am able to connect to the NX server and it authenticates successfully, though after authenticating, I get the following error message (I appologise for the size):

```
NX> 203 NXSSH running with pid: 760
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XX.XX.XX.XX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-8 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: www-data
NX> 102 Password: ********
NX> 103 Welcome to: xxxxxxxxx.com user: www-data
NX> 105 Listsession --user="www-data" --status="suspended\054running" --geometry="1440x900x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: www-data
NX> 105 Start session with: --link="modem" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="serverlfux" --type="unix-gnome" --geometry="1440x872" --client="winnt" --keyboard="pc102\057gb" --screeninfo="1440x872x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 2E7C3711. To get detailed information about
NX> 595 ERROR: the error search for the string 2E7C3711 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```

Here is the nessasery output of my messages file:
```
Dec 15 17:31:47 serverflux NXSERVER-3.3.0-8[21685]: User 'www-data' logged in from '213.137.28.161'. 'NXLogin::set'
Dec 15 17:31:48 serverflux NXSERVER-3.3.0-8[21685]: Selected node host:localhost with port:22 'main::selectNode'
Dec 15 17:31:48 serverflux NXSERVER-3.3.0-8[21685]: Current selected node: localhost is in status: running  'main::selectNode'
Dec 15 17:31:48 serverflux NXSERVER-3.3.0-8[21685]: Selected session type: unix-gnome allowed in the profile of user: www-data 'NXShell::Static'
Dec 15 17:31:48 serverflux NXSERVER-3.3.0-8[21685]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Dec 15 17:31:50 serverflux NXSERVER-3.3.0-8[21685]: A valid NX Server public SSH key is missing on the node. '(eval)'
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.3.0-3  (Error id e113C2B) [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 ERROR: create session: run commands [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 ERROR: execution of last command failed [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 last command: /bin/bash --login -c 'mkdir -p /var/www/.nx/C-serverflux.com-1002-D2C14ADC4602D2A8C02D99D02AF3DA89' [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 exit value: 1 [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 stdout:  [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 stderr: mkdir: cannot create directory `/var/www/.nx': Permission denied [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 . [e113C2B] Logger::log nxnode 2907
Dec 15 17:31:51 serverflux NXNODE-3.3.0-3[21706]: ERROR: NX> 596 init: stdin arguments: user=www%2ddata,userip=213%2e137%2e28%2e161,uniqueid=D2C14ADC4602D2A8C02D99D02AF3DA89,display=1002,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=localhost,balance_host_realip=64%2e86%2e28%2e72,encryption_mode=1,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=serverlfux,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1440x872x32%2brender,keyboard=pc102%2fgb,geometry=1440x872,link=modem Logger::log nxnode 2907
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 ERROR: NXNODE Ver. 3.3.0-3  (Error id e113C2B)
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 ERROR: create session: run commands
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 ERROR: execution of last command failed
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 last command: /bin/bash --login -c 'mkdir -p /var/www/.nx/C-serverflux.com-1002-D2C14ADC4602D2A8C02D99D02AF3DA89'
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 exit value: 1
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 stdout: 
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 stderr: mkdir: cannot create directory `/var/www/.nx': Permission denied
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NX> 596 init: stdin arguments: user=www%2ddata,userip=213%2e137%2e28%2e161,uniqueid=D2C14ADC4602D2A8C02D99D02AF3DA89,display=1002,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=localhost,balance_host_realip=64%2e86%2e28%2e72,encryption_mode=1,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=serverlfux,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1440x872x32%2brender,keyboard=pc102%2fgb,geometry=1440x872,link=modem
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NXNodeExec::exec('startsession', 'user=www%2ddata&userip=213%2e137%2e28%2e161&uniqueid=D2C14ADC460...', 'localhost', 22) called at handlers/nxserver.pl line 3461
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NXShell::handler_session_start('--link="modem" --backingstore="1" --cache="16M" --images="64M" -...') called at NXShell.pm line 373
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NXShell::handle_command('startsession', '--link="modem" --backingstore="1" --cache="16M" --images="64M" -...') called at NXShell.pm line 145
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) NXShell::run() called at nxserver.pl line 4463
Dec 15 17:31:52 serverflux NXSERVER-3.3.0-8[21685]: ERROR: (exception id 2E7C3711) eval {...} called at nxserver.pl line 4422
```

I would greatly appreciate any help on this issue, it has been bugging me for a long while now :D

Thank you

---

### Post by albinootje on 2008-12-16
You should check your posted logfile summary, and fix those errors,
for example this :

mkdir: cannot create directory `/var/www/.nx': Permission denied

The .nx directory is very important.

(Not sure whether you fixed the error about "invalid key" already.)

---

