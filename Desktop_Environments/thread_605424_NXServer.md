---
title: "NXServer"
date: 2007-11-07
forum: Desktop Environments
---

### Post by Inxsible on 2007-11-07
I have installed the NXServer and am trying to connect to it from my XP machine but i keep getting this message:

```
NX> 203 NXSSH running with pid: 4384
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host *<host-name>* port *<port number>*: Connection refused
```Can someone tell me what's wrong please?

The status on my linux box seems ok
```
$sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.
```Thanks

---

### Post by Inxsible on 2007-11-07
bump.

---

### Post by Inxsible on 2007-11-07
If it helps, I have been using the following HowTos to reach where I am at

[http://ubuntuforums.org/showthread.php?t=493983&highlight=install+NXServer](http://ubuntuforums.org/showthread.php?t=493983&highlight=install+NXServer)

[http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/](http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/)


I did change my port to a non standard port because of firewall issues at my work place.

---

### Post by MCMcButtah on 2007-11-07
Outside of using NX, can you ssh from your XP machine to your server? Have you opened that port on your NX server? It sounds like you are trying to connect from work to your home setup...did you make sure that if you have a router that you are forwarding this port to your server from the incomming WAN ip of your work place?

I have been able to get my XP machine to NX to my kubuntu server without a problem using freenx. However, I am only doing this internal on my network.

---

### Post by Inxsible on 2007-11-08
> **MCMcButtah said:**
> Outside of using NX, can you ssh from your XP machine to your server? Have you opened that port on your NX server? It sounds like you are trying to connect from work to your home setup...did you make sure that if you have a router that you are forwarding this port to your server from the incomming WAN ip of your work place?

I have been able to get my XP machine to NX to my kubuntu server without a problem using freenx. However, I am only doing this internal on my network.
How would I test whether I can ssh from my XP to my Ubuntu machine?
Also how would I open that port on my NX server?
I do have an entry for the port number in my router 'Port Forwarding/Port Triggering' section. Is that what you mean?

I cannot even get to my ubuntu machine from within the network using NXServer :(

Please somebody help me out here. I have been at it since the last 3 days now :confused:

There does not seem to be a proper tutorial for NXServer, I found a bunch for FreeNX but I don't know if the same thing applies to NXServer while changing SSH ports etc. 

I even tried it with the default port 22 and it still doesnt work. Gives me 'Connection time out' error

---

### Post by MCMcButtah on 2007-11-08
Try installing putty on your XP box

[http://en.wikipedia.org/wiki/PuTTY](http://en.wikipedia.org/wiki/PuTTY)

NX rides over ssh. When I was first setting up my NX I was having problems as well that I was able to more easily diagnose by first making sure I could do an ssh connection from a command prompt.

If you cannot get to the NXserver from within your own network I would start by getting it working there. 
Have you checked the iptables for your NX server to make sure you allowed this connection? I am pretty sure you will have to specify this so if you have not done that it is most likely your problem. I used the firestarter gui to make this change for me. Firestarter will also show you if the machine has rejected any incoming connections. Iptables is a text file that is basically the firewall rules for the box, firestarter is a frontend that makes changes to this file for you.

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by mrbing on 2008-02-12
Hello if anyone would be able to help me, I have installed the nxserver packages from nomachine and I am not able to connect.

NX> 203 NXSSH running with pid: 7199
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 76.11.165.96 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.1.0-4 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: chris
NX> 102 Password: ***********
NX> 103 Welcome to: chris-desktop user: chris
NX> 105 Listsession --user="chris" --status="suspended\054running" --geometry="1280x1024x24+render" --type="unix-kde" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: chris
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="bytechris.homelinux.com" --type="unix-kde" --geometry="1280x999" --client="linux" --keyboard="pc105\057us" --screeninfo="1280x999x24+render" 
NX> 280 Exiting on signal: 15


It also does not let me enable the user this is the error I receive.

chris@chris-desktop:~$ sudo /usr/NX/bin/nxserver --useradd chris --administrator
NX> 900 Password for user: chris is already set.
NX> 900 Checking user: chris with the NX password DB enabled
NX> 538 Administrator: chris is already in the NX administrator DB.
NX> 900 Adding public key for user: chris to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: chris.

...i know it says i already have added the user but I want to show you the error I got when i first added the user 

It hangs for a while at

NX> 900 Verifying public key authentication for NX user: chris.

NXSERVER - Version 3.1.0-4 - LFE
Tue Feb 12 22:44:55 2008 running as user: 'root' (uid: 0, pid: 6940) on 'chris-desktop'
Info: selected user 'chris' is authenticated (NXNodeExec)
Info: password for selected user is in 'unknown' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name '127.0.0.1', port '22' (NXNodeExec)
Info: selected su to access NX Node (NXNodeExec)
Info: nxssh command line is 'su chris -c /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 6945 (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 1000 NXNODE - Version 3.1.0-6
' (NXNodeExec)
Info: received message 'CONNECTED' from NX Node (NXNodeExec)
Info: sent request for service 'setkey' to NX Node (NXNodeExec)
Info: no parameter to send to NX Node (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 716 Public key is already present in: /home/chris/.ssh/authorized_keys2.
' (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 1001 Bye.
' (NXNodeExec)
Info: received message 'BYE' from NX Node (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec)
Info: connection to NX Node finished correctly (NXNodeExec)
Info: selected user 'chris' is not authenticated no password available (NXNodeExec)
Info: preferred auth method is 'publickey' (NXNodeExec)
Info: selected NX Node with host name '127.0.0.1', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l chris 127.0.0.1 -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 6953 (NXNodeExec)
Error: reached timeout of 60s. Operation in NX Node aborted. (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 1A8A16D2. To get detailed information about
NX> 595 ERROR: the error search for the string 1A8A16D2 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed

I have tried to install nxserver and freenx

I have also used this several times: [http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057)

however it did not work when I reinstalled my machine, I am not quite sure what is different

---

### Post by Inxsible on 2008-04-03
I know your post is over a month old, but you can try this great how to to set up NX Server

[http://ubuntuforums.org/showthread.php?t=736509](http://ubuntuforums.org/showthread.php?t=736509)

---

