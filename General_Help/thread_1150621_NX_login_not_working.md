---
title: "NX login not working"
date: 2009-05-06
forum: General Help
---

### Post by tws on 2009-05-06
Hi there.

I've just set-up my server from scratch, and i can't log in using NX anymore.

I've done everything how i always have; Installed the client, the node and the server.

When i try to login, i get the following error:

```
NX> 148 Server capacity: not reached for user: tws
NX> 105 Start session with: --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="1" --mediahelper="esd" --session="##.##.##.##" --type="unix-gnome" --geometry="1400x1200" --client="winnt" --keyboard="pc102\057ch" --screeninfo="1400x1200x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 76B04E1C. To get detailed information about
NX> 595 ERROR: the error search for the string 76B04E1C in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```

/var/log/messages tells me the following:

```
root@failboat:~# cat /var/log/messages | grep 76B04E1C
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) Warning: Permanently added 'localhost' (RSA) to the list of known hosts.^M
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 ERROR: NXNODE Ver. 3.3.0-17  (Error id eDF6123)
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 ERROR: create session: run commands
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 ERROR: execution of last command failed
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 last command: /bin/bash --login -c 'xauth -v -f /home/tws/.nx/C-failboat-1001-13EF7D244C1CBFFD9F348A6C5AFEE408/authority source /home/tws/.nx/C-failboat-1001-13EF7D244C1CBFFD9F348A6C5AFEE408/scripts/authority'
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 exit value: 1
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 stdout: Using authority file /home/tws/.nx/C-failboat-1001-13EF7D244C1CBFFD9F348A6C5AFEE408/authority
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 Writing authority file /home/tws/.nx/C-failboat-1001-13EF7D244C1CBFFD9F348A6C5AFEE408/authority
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 stderr: xauth:  creating new authority file /home/tws/.nx/C-failboat-1001-13EF7D244C1CBFFD9F348A6C5AFEE408/authority
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 xauth: /home/tws/.nx/C-failboat-1001-13EF7D244C1CBFFD9F348A6C5AFEE408/scripts/authority:3:  bad display name "failboat:1001" in "add" command
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NX> 596 init: stdin arguments: user=tws,userip=##.##.##.##,uniqueid=13EF7D244C1CBFFD9F348A6C5AFEE408,display=1001,node_number=0,server_name=failboat,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=78%2e46%2e96%2e230,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=1,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=78%2e46%2e96%2e230,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1400x1200x32%2brender,keyboard=pc102%2fch,mediahelper=esd,geometry=1400x1200,link=wan
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NXNodeExec::exec('startsession', 'user=tws&userip=##.##.##.##&uniqueid=13EF7D244C1CBFFD9F3...', 'localhost', 22) called at handlers/nxserver.pl line 3533
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NXShell::handler_session_start('--link="wan" --backingstore="1" --encryption="1" --cache="16M" -...') called at NXShell.pm line 373
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NXShell::handle_command('startsession', '--link="wan" --backingstore="1" --encryption="1" --cache="16M" -...') called at NXShell.pm line 145
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) NXShell::run() called at nxserver.pl line 4470
May  6 15:02:10 failboat NXSERVER-3.3.0-22[7361]: ERROR: (exception id 76B04E1C) eval {...} called at nxserver.pl line 4429
root@failboat:~#
```

Doesn't really tell me anything.

Any idea what that is about?

System used is Ubuntu 8.04 LTS x64.

Thanks!

---

### Post by tws on 2009-05-07
Bump.

---

### Post by remyavril on 2011-01-20
Try putting your nxserver's hostname in the /etc/hosts file. Worked right away for me.
Answer can be found here: [http://forums.opensuse.org/english/get-technical-help-here/applications/447785-no-machine-server-configuration-error.html](http://forums.opensuse.org/english/get-technical-help-here/applications/447785-no-machine-server-configuration-error.html)

---

