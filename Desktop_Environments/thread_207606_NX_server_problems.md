---
title: "NX server problems"
date: 2006-07-02
forum: Desktop Environments
---

### Post by rahaal on 2006-07-02
Hi everyone,

I am having problems getting nxserver to accept connections. I have two identical setups (work and home) where i have ubuntu (nxserver) and xp (nxclient) running on the same subnet. Surprisingly, i manged to get the home setup to work perfectly in minutes. The work setup, on the other hand, is a different story. When i try to connect to nxserver locally or remotely i get this error on the client:

NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 1C44C2E2. To get detailed information about
NX> 595 ERROR: the error search for the string 1C44C2E2 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
NX> 500 ERROR: Last operation failed.
Killed by signal 15.

On the sever side i have this:

Jul  2 12:35:23 localhost NXSERVER 2.0.0-69[15531]: WARNING: You appear to run an unsubscribed product. Please visit the 'main::chk_license'
Jul  2 12:35:23 localhost NXSERVER 2.0.0-69[15531]: WARNING: NoMachine Web site at [http://www.nomachine.com/](http://www.nomachine.com/) 'main::chk_license'
Jul  2 12:35:23 localhost NXSERVER 2.0.0-69[15531]: WARNING: to purchase a valid subscription. 'main::chk_license'
Jul  2 12:35:23 localhost NXSERVER 2.0.0-69[15531]: User 'harbks0j' logged in from '10.12.78.207'. 'NXLogin::set'
Jul  2 12:35:26 localhost NXSERVER 2.0.0-69[15531]: Selected node host:localhost (ip: 10.12.78.207) with port:22 'main::selectNode'
Jul  2 12:35:26 localhost NXSERVER 2.0.0-69[15531]: Current selected node: 10.12.78.207 is in status: running  'main::selectNode'
Jul  2 12:35:28 localhost NXNODE 2.0.0-93[15548]: DEBUG: You appear to run an unsubscribed product. Please visit the 'main:nxnode:2513'
Jul  2 12:35:28 localhost NXNODE 2.0.0-93[15548]: DEBUG: NoMachine Web site at [http://www.nomachine.com/](http://www.nomachine.com/) 'main:nxnode:2514'
Jul  2 12:35:28 localhost NXNODE 2.0.0-93[15548]: DEBUG: to purchase a valid subscription. 'main:nxnode:2515'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.0.0-93  (Error id e419A84) [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 ERROR: Sun Jul  2 12:35:29 2006 running as user: 'harbks0j' (uid: 1000) on '' [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 ERROR: execution of last command failed [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/harbks0j/.nx/C-figrah-1007-DD2AFBA1BB3CB04FCC3C5D93BF27858E/scripts/authority' [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 exit value: 1 [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 stdout:  [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 stderr: xauth:  error in locking authority file /home/harbks0j/.Xauthority [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 . [e419A84] 'main:nxnode:2662'
Jul  2 12:35:29 localhost NXNODE 2.0.0-93[15548]: ERROR: NX> 596 init: stdin arguments: user=harbks0j,userip=10%2e12%2e78%2e207,uniqueid=DD2AFBA1BB3CB04FCC3C5D93BF27858E,display=1007,license=%28None%29,subscriptionid=None,productid=LDS,reconnect=1,balance_host=10%2e12%2e78%2e207,encryption_mode=1,images=32M,cache=8M,client=linux,media=0,backingstore=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=localhost,shmem=1,type=unix%2dgnome,virtualdesktop=1,nodelay=1,screeninfo=800x600x16%2brender,streaming=1,keyboard=pc102%2fus,geometry=800x600%2b240%2b187,link=lan 'main:nxnode:2662'
Jul  2 12:35:30 localhost NXNODE 2.0.0-93[15548]: INFO: getting agent pid: cannot read pid file '/home/harbks0j/.nx/C-figrah-1007-DD2AFBA1BB3CB04FCC3C5D93BF27858E/pids/agent'. Exiting. 'main:nxnode:7857'
Jul  2 12:35:30 localhost NXNODE 2.0.0-93[15548]: INFO: directory '/home/harbks0j/.nx/C-figrah-1007-DD2AFBA1BB3CB04FCC3C5D93BF27858E' moved into '/home/harbks0j/.nx/F-C-figrah-1007-DD2AFBA1BB3CB04FCC3C5D93BF27858E' for investigation 'main:nxnode:7912'
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 ERROR: NXNODE Ver. 2.0.0-93  (Error id e419A84)
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 ERROR: Sun Jul  2 12:35:29 2006 running as user: 'harbks0j' (uid: 1000) on ''
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 ERROR: in node start session: create session: run commands
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 ERROR: execution of last command failed
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/harbks0j/.nx/C-figrah-1007-DD2AFBA1BB3CB04FCC3C5D93BF27858E/scripts/authority'
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 exit value: 1
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 stdout:
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 stderr: xauth:  error in locking authority file /home/harbks0j/.Xauthority
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NX> 596 init: stdin arguments: user=harbks0j,userip=10%2e12%2e78%2e207,uniqueid=DD2AFBA1BB3CB04FCC3C5D93BF27858E,display=1007,license=%28None%29,subscriptionid=None,productid=LDS,reconnect=1,balance_host=10%2e12%2e78%2e207,encryption_mode=1,images=32M,cache=8M,client=linux,media=0,backingstore=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=localhost,shmem=1,type=unix%2dgnome,virtualdesktop=1,nodelay=1,screeninfo=800x600x16%2brender,streaming=1,keyboard=pc102%2fus,geometry=800x600%2b240%2b187,link=lan
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NXNodeExec::exec('startsession', 'user=harbks0j&userip=10%2e12%2e78%2e207&uniqueid=DD2AFBA1BB3CB04...', 10.12.78.207, 22) called at handlers/nxserver.pl line 2809
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NXShell::handler_session_start('--link="lan" --backingstore="1" --streaming="1" --nodelay="1" --...') called at NXShell.pm line 374
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NXShell::handle_command('startsession', '--link="lan" --backingstore="1" --streaming="1" --nodelay="1" --...') called at NXShell.pm line 145
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) NXShell::run() called at nxserver.pl line 4438
Jul  2 12:35:30 localhost NXSERVER 2.0.0-69[15531]: ERROR: (exception id 1C44C2E2) eval {...} called at nxserver.pl line 4397

Appreciate all the help I can get.


Regards,

---

### Post by thk on 2007-05-13
Is xauth installed on the server? It is necessary for X11 forwarding with ssh. If it still does not work, please check /var/log/auth.log for missing symbols in libcrypto. That is the error I am getting and would like to know if others see the same.

---

