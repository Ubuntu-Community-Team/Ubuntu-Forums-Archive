---
title: "Remote desktop - NX Server"
date: 2013-07-18
forum: Desktop Environments
---

### Post by bamby1607 on 2013-07-18
I'm trying to  login  remotely to my Ubuntu (12.04) desktop by using  NX Client program ( running on Windows 7 laptop). On the Ubuntu box NX server (version 3.5) is configured to use SSH which is also installed on the box.


I was able to login with no issues all these days but since today morning the client is throwing an error and unable to login to the box. Between last night and today morning  I have only changed two files -  /etc/hosts & /etc/hostname. After the change both files reads as follows


```



127.0.0.1 localhost
127.0.1.1 name_of_host



```




Please note that the ubuntu box has LAMP running on it.


I looked at the syslog on the Ubuntu box  and this the log message I get


```



Jul 16 08:50:32 (none) NXSERVER-3.5.0-11[2717]: ERROR: Wrong hostname get from hostname command: hostname 


cannot be 127.0.0.1localhost\n127.0.1.1 name_of_host\n. Falling down to 'localhost' 


'main::defineServerName'
Jul 16 08:50:32 (none) NXSERVER-3.5.0-11[2717]: User 'anirban' logged in from '192.168.1.166'. 


'NXLogin::set'
Jul 16 08:50:32 (none) NXSERVER-3.5.0-11[2717]: Selected node host:localhost with port:22 


'main::selectNode'
Jul 16 08:50:32 (none) NXSERVER-3.5.0-11[2717]: Current selected node: localhost is in status: running  


'main::selectNode'
Jul 16 08:50:32 (none) NXSERVER-3.5.0-11[2717]: Selected session type: unix-gnome allowed in the profile of 


user: anirban 'NXShell::Static'
Jul 16 08:50:35 (none) NXSERVER-3.5.0-11[2717]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jul 16 08:50:35 (none) NXNODE-3.5.0-9[3015]: ERROR: Wrong hostname get from hostname command: hostname 


cannot be 127.0.0.1localhost\n127.0.1.1 name_of_host\n. Falling down to 'localhost' Logger::log nxnode 4022
Jul 16 08:50:35 (none) NXSERVER-3.5.0-11[2717]: A valid NX Server public SSH key is missing on the node. 


'(eval)'
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.5.0-9  (Error id eA00522) 


[eA00522] Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 ERROR: create session: run commands [eA00522] 


Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 ERROR: execution of last command failed 


[eA00522] Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 last command: /usr/bin/xauth -v -f 


/home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority source /home/anirban/.nx/C-


localhost-1045-92F48869E466AA2AA181EEF0895EA441/scripts/authority [eA00522] Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 exit value: 1 [eA00522] Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 stdout: Using authority file 


/home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority [eA00522] Logger::log nxnode 


2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 Writing authority file /home/anirban/.nx/C-


localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority [eA00522] Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 stderr: /usr/bin/xauth:  file 


/home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority does not exist [eA00522] 


Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 /usr/bin/xauth: /home/anirban/.nx/C-localhost-


1045-92F48869E466AA2AA181EEF0895EA441/scripts/authority:3:  bad "add" command line [eA00522] Logger::log 


nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 /usr/bin/xauth: /home/anirban/.nx/C-localhost-


1045-92F48869E466AA2AA181EEF0895EA441/scripts/authority:4:  unknown command "127.0.1.1" [eA00522] 


Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 . [eA00522] Logger::log nxnode 2963
Jul 16 08:50:37 (none) NXNODE-3.5.0-9[3015]: ERROR: NX> 596 init: stdin arguments: 


user=anirban,userip=192%2e168%2e1%2e166,uniqueid=92F48869E466AA2AA181EEF0895EA441,display=1045,node_number=


0,server_name=localhost,license=%28None


%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e1%2e109,encryption_mode=3,connec


tion=local,images=64M,cache=16M,client=winnt,media=1,backingstore=1,encryption=1,strict=0,clipboard=both,sh


pix=1,rootless=0,composite=1,session=name_of_host,shmem=1,type=unix


%2dgnome,virtualdesktop=1,screeninfo=1600x900x32%2brender


%2bfullscreen,keyboard=pc105%2fen_US,mediahelper=esd,fullscreen=1,geometry=1594x832,link=lan,samba=1 


Logger::log nxnode 2963
Jul 16 08:50:38 (none) NXNODE-3.5.0-9[3015]: getting agent pid: cannot read pid file '/home/anirban/.nx/C-


localhost-1045-92F48869E466AA2AA181EEF0895EA441/pids/agent'. Exiting. main::get_agent_pid nxnode 9042
Jul 16 08:50:38 (none) NXNODE-3.5.0-9[3015]: directory '/home/anirban/.nx/C-localhost-1045-


92F48869E466AA2AA181EEF0895EA441' moved into '/home/anirban/.nx/F-C-localhost-1045-


92F48869E466AA2AA181EEF0895EA441' for investigation Logger::log nxnode 9099
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 ERROR: NXNODE Ver. 


3.5.0-9  (Error id eA00522)
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 ERROR: create 


session: run commands
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 ERROR: execution of 


last command failed
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 last command: 


/usr/bin/xauth -v -f /home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority source 


/home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/scripts/authority
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 exit value: 1
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 stdout: Using 


authority file /home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 Writing authority 


file /home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 stderr: 


/usr/bin/xauth:  file /home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/authority does 


not exist
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 /usr/bin/xauth: 


/home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/scripts/authority:3:  bad "add" command 


line
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 /usr/bin/xauth: 


/home/anirban/.nx/C-localhost-1045-92F48869E466AA2AA181EEF0895EA441/scripts/authority:4:  unknown command 


"127.0.1.1"
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NX> 596 init: stdin 


arguments: 


user=anirban,userip=192%2e168%2e1%2e166,uniqueid=92F48869E466AA2AA181EEF0895EA441,display=1045,node_number=


0,server_name=localhost,license=%28None


%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e1%2e109,encryption_mode=3,connec


tion=local,images=64M,cache=16M,client=winnt,media=1,backingstore=1,encryption=1,strict=0,clipboard=both,sh


pix=1,rootless=0,composite=1,session=name_of_host,shmem=1,type=unix


%2dgnome,virtualdesktop=1,screeninfo=1600x900x32%2brender


%2bfullscreen,keyboard=pc105%2fen_US,mediahelper=esd,fullscreen=1,geometry=1594x832,link=lan,samba=1
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NXNodeExec::exec


('startsession', 'user=anirban&userip=192%2e168%2e1%2e166&uniqueid=92F48869E466AA2...', 'localhost', 22) 


called at handlers/nxserver.pl line 3582
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) 


NXShell::handler_session_start('--link="lan" --backingstore="1" --encryption="1" --cache="16M" -...') 


called at NXShell.pm line 373
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NXShell::handle_command


('startsession', '--link="lan" --backingstore="1" --encryption="1" --cache="16M" -...') called at 


NXShell.pm line 145
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) NXShell::run() called at 


nxserver.pl line 4497
Jul 16 08:50:38 (none) NXSERVER-3.5.0-11[2717]: ERROR: (exception id 6DF53054) eval {...} called at 


nxserver.pl line 4456





```




Any help is really appreciated.

---

### Post by theDaveTheRave on 2013-07-18
bamby1607,

are you able to rever to the original version of the files, just to confirm that it is this modification that has 'broken' your nx server config.

I seem to recall that the nx server (running on the box that you are wanting to log into - in your case the ubuntu 12.04 lamp server) has a config setting for the exected IP address of the current machine, I can't check my nx config as i'm not home at the mo, as you have modified these 2 files you may have inadvertently told your server to listen only on these 2 ip's.

On your server run a ```
netstat
``` to show the open ports (you'll need sudo), and check the the true ip address of this terminal with and ```
ifconfig
```

---

