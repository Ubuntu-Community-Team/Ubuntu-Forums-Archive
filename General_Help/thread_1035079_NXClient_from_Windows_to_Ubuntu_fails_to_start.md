---
title: "NXClient from Windows to Ubuntu fails to start"
date: 2009-01-09
forum: General Help
---

### Post by RoGGeR on 2009-01-09
Hi All,

I have a very strange problem with NXClient - nxclient-3.2.0-13.exe when try to connect from Windows to Ubuntu.
First time or the first several times (2-3) it always fails, but at the end I succeed to connect.

I followed the instructions to set the

SESSION_LOG_CLEAN=0 in node.conf

plus two additional parameters:

NX_LOG_LEVEL=7
NX_LOGFILE=/var/log/nxserver.log

And this is the output of the nxserver.log file:

-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: mike
NX> 102 Password: 
Info: Auth method: passdb ssh 
NX> 103 Welcome to: ubuntu user: mike
NX> 105 listsession --user="mike" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'mike' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: mike
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Ubuntu" --type="unix-gnome" --geometry="1280x996" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x996x32+render" 

Info: Using /usr/lib/nx/nxacl to change session parameters or deny session.
&link=lan&backingstore=1&encryption=1&cache=8M&images=32M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=Ubuntu&type=unix-gnome&geometry=1280x996&client=winnt&keyboard=pc102/en_US&screeninfo=1280x996x32+render&clientproto=2.1.0&user=mike&userip=192.168.0.3&uniqueid=C5436ACD34696C1AB0088075CDD3C2E9&display=1001&host=127.0.0.1 
mike@127.0.0.1's password: 
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: ubuntu-1001-C5436ACD34696C1AB0088075CDD3C2E9
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: aea6606cbc8218d14dd60badd1b80ac9
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: aea6606cbc8218d14dd60badd1b80ac9
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: ubuntu-1001-C5436ACD34696C1AB0088075CDD3C2E9
server_nxnode_echo: NX> 705 Session display: 1001
server_nxnode_echo: NX> 703 Session type: unix-gnome
server_nxnode_echo: NX> 701 Proxy cookie: aea6606cbc8218d14dd60badd1b80ac9
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie: aea6606cbc8218d14dd60badd1b80ac9
server_nxnode_echo: NX> 704 Session cache: unix-gnome
server_nxnode_echo: NX> 707 SSL tunneling: 1
/usr/lib/nx/nxnode: line 542:  6259 Terminated              PATH="$PATH_BIN:$PATH" $PATH_BIN/nxagent $P $R -name "NX - $user@$SERVER_NAME:$display - $session (GPL Edition)" -option "$USER_FAKE_HOME/.nx/C-$sess_id/options" $K $G $B $FP $AGENT_EXTRA_OPTIONS_X :$display 2>&3
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/mike/.nx/F-C-ubuntu-1001-C5436ACD34696C1AB0088075CDD3C2E9/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 105 NX> 1006 Session status: closed
xrdb: No such file or directory
xrdb: Can't open display ':1001'

(gnome-session:6270): Gtk-WARNING **: cannot open display: :1001
server_nxnode_echo: NX> 596 Session startup failed.
NX> 596 Session startup failed.
server_nxnode_echo: NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/mike/.nx/F-C-ubuntu-1001-C5436ACD34696C1AB0088075CDD3C2E9/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
session_close C5436ACD34696C1AB0088075CDD3C2E9
server_nxnode_echo: NX> 1006 Session status: closed
NX> 1001 Bye.
server_nxnode_echo: NX> 1001 Bye.
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: mike
NX> 102 Password: 
Info: Auth method: passdb ssh 
NX> 103 Welcome to: ubuntu user: mike
NX> 105 listsession --user="mike" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'mike' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: mike
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Ubuntu" --type="unix-gnome" --geometry="1280x996" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x996x32+render" 

Info: Using /usr/lib/nx/nxacl to change session parameters or deny session.
&link=lan&backingstore=1&encryption=1&cache=8M&images=32M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=Ubuntu&type=unix-gnome&geometry=1280x996&client=winnt&keyboard=pc102/en_US&screeninfo=1280x996x32+render&clientproto=2.1.0&user=mike&userip=192.168.0.3&uniqueid=77C2EB174EAC40626A09FF4BF22AF3DF&display=1001&host=127.0.0.1 
mike@127.0.0.1's password: 
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: ubuntu-1001-77C2EB174EAC40626A09FF4BF22AF3DF
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 80660855a7e7d83587b2a1623ae07a32
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 80660855a7e7d83587b2a1623ae07a32
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: ubuntu-1001-77C2EB174EAC40626A09FF4BF22AF3DF
server_nxnode_echo: NX> 705 Session display: 1001
server_nxnode_echo: NX> 703 Session type: unix-gnome
server_nxnode_echo: NX> 701 Proxy cookie: 80660855a7e7d83587b2a1623ae07a32
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie: 80660855a7e7d83587b2a1623ae07a32
server_nxnode_echo: NX> 704 Session cache: unix-gnome
server_nxnode_echo: NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
server_nxnode_echo: NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
server_nxnode_echo: NX> 710 Session status: running
server_nxnode_echo: NX> 1002 Commit
session_status 77C2EB174EAC40626A09FF4BF22AF3DF Running
NX> 105 server_nxnode_echo: NX> 1006 Session status: running
bye
Bye
NX> 999 Bye

Please help if you have any idea.

I am changing my current Home Server OS from Free BSD to Ubuntu and I want to be sure that everything is working smoothly.

Thanks in Advance,

Best Regards

---

