---
title: "NXserver"
date: 2006-06-27
forum: Desktop Environments
---

### Post by The Devil Is A Squirrel on 2006-06-27
Hi everybody

I am actually a bit frustrated...spend hours to get run nxserver  but with no real luck...

I followed [this]("http://neorazorx.homeunix.org/wiki/index.php/NX") guide (but I let the port by 22) and now I get the following message when I try a local connection (localhost):

```
NX> 203 NXSSH running with pid: 25229
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 127.0.0.1 on port: 22
NX> 211 The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 88:b6:f1:ae:9:5b:e0:a3:fc:7c.
Are you sure you want to continue connecting (yes/no)? 
Failed to add the host to the list of known hosts (/home/squirrel/.ssh/known_hosts).
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: squirrel
NX> 102 Password: 
NX> 103 Welcome to: squirrel-desktop user: squirrel
NX> 105 listsession --user="squirrel" --status="suspended,running" --geometry="1920x1200x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'squirrel' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: squirrel
NX> 105 startsession --session="me" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbtype="pc105/de" --nodelay="1" --backingstore="when_requested" --geometry="1024x768+448+190" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1024x768x24+render" 

Permission denied (publickey,password).
Killed by signal 15.

```

Can anyone help me?

Any help or hint would be very appreciated.

---

### Post by jkbrowne on 2006-06-28
Ok, I've fought with this off and on for a-while, but I finally found the right combination.  First of all, forget freeNX.  The NoMachine folks have released a "desktop" edition of their latest product called "NX Desktop Server" that is free for personal use (2 users/connections).  

Before proceeding, be sure to *completely* remove any previous versions of any of the FreeNX files or libraries.  Undo what you have already done, and remove the FreeNX source URLs from your /etc/apt/sources.list.


-----------------------
Step 1 - Download
-----------------------

Download "NX Desktop Server DEB for Linux" from:
[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Download "NX Node DEB for Linux" from:
[http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

Download "NX Client DEB for Linux" from:
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

-----------------------
Step 2 - Install
-----------------------
Install the DEB files in this order:

nxclient
nxnode
nxserver

I just right-clicked on them and installed them...use apt-get if you prefer.

-----------------------
Step 3 - Configure
-----------------------
Load up your /etc/ssh/sshd_config file into an editor:

sudo nano /etc/ssh/sshd_config

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart

Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status

This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration.  If not, then NX Desktop Server should be installed.

Before anyone complains, yes, I'm using the NoMachine server key just because it's easy.  If you want to generate your own key, you can.  These instructions worked for me on Dapper....YMMV.  Let me know if you have trouble.....hopefully my notes were correct.

Good luck!

---

### Post by The Devil Is A Squirrel on 2006-06-28
Hi jkbrowne

Thank you so much for your help! It's quite frustrating with those dozens different guides that not work. I think I am almost there, after the handshake I get the following message  


and then the message details...


```


Info: Display running with pid '2748' and handler '0x150372'.
NXPROXY - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '3400'.
Session: Starting session at 'Wed Jun 28 10:38:18 2006'.
Info: Connecting to remote host '84.72.175.164:5002'.
Info: Aborting the procedure due to signal '15'.
Error: Couldn't kill the dialog process with pid '1960'.
Session: Session terminated at 'Wed Jun 28 10:38:48 2006'.

```

What did I wrong? Can you help me one more time?



Update
====
Maybe it's the DMZ from my company...but I tried it actually with another PC outside the LAN and get the following failure

```
Info: Proxy running in client mode with pid '356'.
Session: Starting session at 'Wed Jun 28 21:37:50 2006'.
Info: Connecting to remote host '217.16.104:5008'.
Info: Connection to remote proxy '217.16.104:5008' established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using adsl link parameters 512/24/1/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/2048/256.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using product 'LDS/None/LDSN/None'.
Info: Using ZLIB data compression 3/3/0.
Info: Using ZLIB stream compression 6/6.
Info: No suitable cache file found.
Info: Using remote server '217.162.104:5008'.
Info: Listening for font server connections on port '11008'.
Session: Session started at 'Wed Jun 28 21:37:51 2006'.
Error: Connection to ':0' failed. Error is 2 'No such file or directory'.
Error: Failure reading from the peer proxy.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Session terminated at 'Wed Jun 28 21:37:55 2006'.
```

The network was just fine. What's wrong?

---

### Post by gurgle on 2006-06-28
evan@evan-ubuntu:~$ /etc/init.d/ssh restart
bash: /etc/init.d/ssh: No such file or directory


Anything?

---

### Post by jongep86 on 2006-06-28
Works great!!! I had it up and running in 3 minutes. Know I can connect from my Gentoo laptop to my Ubuntu dapper workstation. Thank you very much

---

### Post by jkbrowne on 2006-06-28
gurgle:

Sorry, I forgot to mention that you need the ssh package installed beforehand.  Be sure it's installed, and then you should be able to continue with the NX installation instructions.

---

### Post by jkbrowne on 2006-06-28
Squirrel:

You definitely should be testing the connection locally (at home), to eliminate firewalls from the equation.

Are you running it on the default port 22?

I'm not sure what's up exactly, but looking at one of your logs:

Info: Connecting to remote host '217.16.104:5008'.

The ip address is missing the 4th octet....this says to me it's attempting to connect to 217.16.104 (which is an incomplete ip address).  Check your configuration & verify the address is correct.

---

### Post by The Devil Is A Squirrel on 2006-06-28
Hi jkbrowne

yeah, that's correct because I had removed the digits in the post (maybe paranoid)...  :cool: 

Actually I remove everything and try it again...

Thanks for your help!!   =D>


Update
====
Finally! It runs local, now I will test the remote part...

Question: Will it work in a DMZ or other firewalled environment? Or is it "just like" VNC?

---

### Post by thk on 2006-06-28
Why do they insist on installing in /usr/NX? Very annoying.

---

### Post by jkbrowne on 2006-06-28
Not sure....but I agree, it shouldn't go to /usr/NX.  /opt/NX would be my vote, based on the FHS standard.

---

### Post by jkbrowne on 2006-06-28
Squirrel,

Glad to hear you have it working locally.  It should work from anywhere, as long as you can access the port you are running NX server/ssh (typically port 22).

---

### Post by The Devil Is A Squirrel on 2006-06-29
[QUOTE=jkbrowne]Squirrel,

Glad to hear you have it working locally.  It should work from anywhere, as long as you can access the port you are running NX server/ssh (typically port 22).[/QUOTE]

It works through our DMZ but only with encryption...  :grin: 

[SIZE="3"]**jkbrowne, thank you very very much!**[/SIZE]  =D>   =D>

---

### Post by volvoguy on 2006-06-29
Do we need to run the command to generate (or import or whatever) the NoMachine key? I don't seem to have:

AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

In fact, no ".ssh" directory at all (and I do have SSH installed and working on a daily basis). The only other hickup I ran into was the fact that I disabled CUPS on the server (not a printer in sight) and nxnode complained but seemed to install ok regardless. When I try to connect I get a popup and more details in the failure message. The popup says:

"The connection with the remote server was shut down. Please check the state of your network connection."

(the connection is fine, the machines are right next to each other and plugged into the same 100mb switch). I have an SSH session opened to the server so I know it isn't network troubles. If I click on the failure message, the details say this:

Info: Display running with pid '1432' and handler '0x2b0212'.
NXPROXY - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '3888'.
Session: Starting session at 'Thu Jun 29 14:20:21 2006'.
Info: Connecting to remote host '192.168.1.11:5001'.
Info: Connection to remote proxy '192.168.1.11:5001' established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using modem link parameters 256/24/1/0.
Info: Using cache parameters 4/4194304/32768KB/32768KB.
Info: Using image streaming parameters 50/128/1024KB/1024/128.
Info: Using image cache parameters 1/1/65536KB.
Info: Using pack method '16m-jpeg-3' with session 'unix-gnome'.
Info: Using product 'LDS/None/LDSN/None'.
Info: Using ZLIB data compression 6/6/0.
Info: Using ZLIB stream compression 9/9.
Info: No suitable cache file found.
Info: Using remote server '192.168.1.11:5001'.
Info: Listening for font server connections on port '11001'.
Session: Session started at 'Thu Jun 29 14:20:21 2006'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Session terminated at 'Thu Jun 29 14:20:21 2006'.


Because there were a few annoying behaviors in the freenx stuff, I'd really like to use this new "free" NoMachine server. I guess we need an all encompassing How-To for using this new software! Keep up the conversation!

Thanks!

Aaron

---

### Post by The Devil Is A Squirrel on 2006-06-29
Hi Aaron

I had the same problem as you. You installed the freenx right? First make sure that the freenx stuff is completely removed. Remove it with "apt-get uninstall" and then all the application which you had installed . Then delete every freenx folder in the system. Make sure that the sshd file in /etc/ssh/ has the original settings (port 22 and so on). Then install the "real" nx as guided from jkbrowne before. Do it exactly as described. Now it should work (it worked for me only with enabled ssl-encryption).


You want to see the key files in the .shh folder? 

1. Got to [this]("http://ubuntuguide.org/wiki/Dapper") page and search the following sentence "How to open files as root user via right click", do it as described.

2. Go to the following path: /usr/NX/home

3. You will see an folder named "nx" with a red cross. Right click on it and choose "Scripts / open as root". Type in your root password. A new window will open. Then go to the menu and click on "Go" and choose "Location...". Type in the adress-bar "/usr/NX/home/nx/.ssh", now you should see the files...

---

### Post by volvoguy on 2006-06-29
Thanks T.D.I.A.S. (hehe)

I've got everything you suggested covered. The only difference is trivial I think - I used "apt-get remove --purge" to uninstall all the freenx stuff. I'm thinkin' it's something SSH related, since the session actually starts, but closes immediately telling me there's a network problem. (it's definitely not a *physical* network problem). 

Any other thoughts? I know the NX server is running:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

And I restarted SSH after editing the config file. What about the "key" button in the client config? With freenx I didn't need to copy any key files over to the client machine, but perhaps I do for this version? *shrug* I'm stumped. 

Thanks!

Aaron
----------------
Ubuntu SVG Wallpapers - [http://www.volvoguy.net/ubuntu](http://www.volvoguy.net/ubuntu)

---

### Post by The Devil Is A Squirrel on 2006-06-30
Hi Aaron

Yes, I had the same issue. And I have it still but only part wise and I don't know why.

Situation A: I can connect inside a secure company (with DMZ and so on) **with SSL-Encryption** with no problem to my pc at home.

Situation B: My father (actually me over VNC) can't connect from his normal pc with a simple adsl-router (yes, port 22 and 5000 is forwarded) to my pc. It shows after the handshake a message that there exists a network problem (or a text like "server was shutting down").

I will track the problem..hoping to find out something...

Aaron, have you tried under the tab "Advanced" to enable the SSL-Encryption?

---

### Post by volvoguy on 2006-06-30
Yeah, this one is buggin' the heck out of me. I've tried with and without encryption - no difference. Just says to check my network connections. I'm copying a 4Gb file from the NX server (via Samba) so I know the network is just fine.

The weird thing is - the session actually starts! If I retry the connection it bumps up the NX port number each time (1000, 1001, etc). Almost immediately afterward though, it closes with the network error. I haven't physically restarted the NX server machine in a while. I shouldn't have to, but maybe I'll give it a go later once I get some sleep. I wish the NoMachine folks had a little more documentation. Hopefully it'll improve a bit now that they've made their server free for personal use. Right now they don't tell you much more than how to install a .deb file with dpkg.

If you NoMachine people are following this thread though, I sincerely thank you for opening things up a bit. Once all the kinks are worked out I think this is going to work a bit better than the FreeNX packages (no offense to the FreeNX people either!). 

Aaron

---

### Post by The Devil Is A Squirrel on 2006-06-30
I give it up. It works thourgh the DMZ but through a simple ADSL/Router (yes, the ports are forwarded) it just not works...I get every time the message that "The connection to the remote server was shut down. check your network connection..."

Just a brain-flash: Could it be that the client needs service packs on windows xp? At the company we have windows xp with sp2, my father has no service packs at all...

---

### Post by brakmaren on 2006-06-30
Thank's for this one. Almost as simple as getting it from repos :D 
Only one problem here. 
When i connect i get
> The authenticity of host x.x.x.x can't be established.
RSA key fingerprint is (a lot of numbers).
Are you sure you want to continue?
If i choose yes it connects like a sharm, so no problems there.
Just would like to get rid of the authenticity failure.
Any solutions?
Thank's

---

### Post by volvoguy on 2006-07-01
[QUOTE=brakmaren]
If i choose yes it connects like a sharm, so no problems there.
Just would like to get rid of the authenticity failure.
Any solutions?
Thank's[/QUOTE]

That's a pretty standard information message when connecting to a server via SSH for the first time. If you get it EVERY time you're connecting the same client to the same server, it might be something to investigate further, but in general it's just information. The client is saying, "I don't know this server. Is it safe to connect?". 

I've been known to be wrong once or twice in my life though, so if you know a different answer, speak up! :-) 

Aaron

---

### Post by brakmaren on 2006-07-01
Thank's mate.
Yesterday i got it every time i logged in. This morning it whas gone after first login.
Guess she just needed some sleep :smile: 
Thank's for the quick input.

---

### Post by matko on 2006-07-07
> **jkbrowne said:**
> Squirrel,

Glad to hear you have it working locally.  It should work from anywhere, as long as you can access the port you are running NX server/ssh (typically port 22).

i had the sam problem. now it works. i had to use SSL.
but have amiother problem. a connect (probably) cause no error.
but i cant see any window or anything indicates my lovely ubuntu.
i see only service running in background.
where i did mistake?

thanx to all

---

### Post by Dgurion on 2006-07-10
Umm, I followed your instructions and the server is up and running.. But whenever I try to connect to it from my windows laptop it asks if im sure I wanna connect (beacause the authenticity can't be established) and I hit yes and after that it just timesout everytime..

---

### Post by sweatherly on 2006-07-10
I'm in the same boat as Dgurion - followed the installation instructions but I receive a timeout in NX Client after clicking the 'Yes' button for the authenticity question.

My client log reads:[INDENT]
NX> 203 NXSSH running with pid: 2224
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.60 on port: 22
NX> 211 The authenticity of host '192.168.1.60 (192.168.1.60)' can't be established.
RSA key fingerprint is b7:9a:8d:2f:ad:74:a9:b4:5c:4c:9f:c9:90:77:9a:85.
Are you sure you want to continue connecting (yes/no)? [/INDENT]
Not sure what's up. I can successfully attach to my Ubuntu box with Putty on port 22 from my Windows machine. I can also successfully connect if I run an NX Client on my Ubuntu installation and connect to localhost. Just don't seem to be able to connect with NX Server on Ubuntu and NX Client on Windows.

Any help much appreciated...

---

### Post by Dgurion on 2006-07-11
Yeah, Thats the exact problem im experiencing.. Sigh..

---

### Post by sweatherly on 2006-07-11
Dgurion, just out of interest are you using Xgl? I couldn't get VNC to work with Xgl which is how I actually come to trying NX. Maybe Xgl is still causing us a problem (although it's hard to see how given I can attach with Putty and attach with an NX client locally)?

I get the same problem if I disable my Windows firewall. Both of my computers are on my LAN so the problem's not router related :-(

---

### Post by Dgurion on 2006-07-11
No, I dont have XGL installed.. Its a rather weird problem.. I wish it gave more info other than just a timeout error...

---

### Post by Brbotalnik on 2006-07-11
Im running sshd on a custom port and I really can't figure out how to configure nomachine nx desktop to work with ssh.
Has anyone successfully installed nx desktop with ssh not running on port 22 ?

Many thanks for any help.
Bye.

---

### Post by Brbotalnik on 2006-07-11
In fact I somehow managed to get things working. I've changed in nxserver.cfg and nxnode.cfg files SSHD PORT and in spite of many errors when a new user is added it magicaly works.

---

### Post by ethridgt on 2006-08-04
Volvoguy, I have your solution.  Well, at least I hope I do.  I was having the exact same problem as you.  This is a version of Ubuntu that I have upgraded since Hoary.  The problem had to do with the font paths. 

Check out ~/.nx/<some-unique-directory-name>/status.  Mine had a line that read fatal server error, could not find font 'fixed'.  The unique name is just random letters and numbers.  It creates a new directory each time.

I had to modify /usr/NX/etc/node.cfg.  I added this line:

AGENT_EXTRA_OPTIONS_X="-fp /usr/share/X11/fonts/misc:/usr/share/X11/fonts/cyrillic:/usr/share/X11/fonts/Type1:/usr/share/X11/fonts/CID:/usr/share/X11/fonts/100dpi:/usr/share/X11/fonts/75dpi:/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType:/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

I restarted the nxserver and then it worked.  I hope this helps.

$ sudo /usr/NX/bin/nxserver --stop
$ sudo /usr/NX/bin/nxserver --start

-- tale :)

---

### Post by andersja on 2006-08-08
I followed the tutorial and when doing the last step - the local test - I get the success message; however when trying to connect from a windows box using the latest nxclient for windows, I get:

```
Info: Display running with pid '0' and handler '0x65'.
NXPROXY - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '3988'.
Session: Starting session at 'Wed Aug  9 03:12:51 2006'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Error: Function fork failed with result '-1'. Error is 11 'Resource temporarily unavailable'.
Error: Failed to execute the X auth command. Error is 11 'Resource temporarily unavailable'.
Error: Cannot read the cookie from the authorization file.
Error: Error creating the X authorization.
Session: Session terminated at 'Wed Aug  9 03:12:51 2006'.
Warning: Signals were already blocked in process with pid '3988'.


```

Any ideas? Could it be linked to the fact that I'm already logged in with a Gnome session on the console of this box?

---

### Post by andersja on 2006-08-09
Some additional information - when I go to my ~/.nx directory, I find a subdirectory per failed session. Opening it, I find:

```
$ cat session
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

NXAGENT - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid '32713'.
Session: Starting session at 'Wed Aug  9 10:35:12 2006'.
Info: Proxy running in server mode with pid '32713'.
Info: Waiting for connection from '192.168.1.101' on port '5004'.
Info: Accepted connection from '192.168.1.101' with port '55695'.
Info: Connection with remote proxy established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using isdn link parameters 384/24/1/0.
Info: Using agent parameters 5000/50/0/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/1536/192.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-5' with session 'unix-gnome'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 6/6/32.
Info: Using ZLIB stream compression 9/9.
Info: No suitable cache file found.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.

Fatal server error:
Error: Unable to open display 'nx/nx,options=/home/username/.nx/C-servername-1004-7F39881E8F0AA7552592ADF4878854E8/options:1004'.

```

My network is just fine; I can successfully ssh to the box from the outside world using putty. My firewall (in my router) blocks all inbound requests bar port 22 and 443.

---

### Post by Harry_Sack on 2006-08-09
:D Thank you.
This worked without any problems

---

### Post by Dgurion on 2006-08-11
Does anyone have a solution to the problem I posted earlier? Still trying to figure out how to make it work properly...

---

### Post by A-star on 2006-08-12
thanks for the howto, it just works great here

---

### Post by Soarer on 2006-08-14
I had the previous version working fine. Removed it all, installed client, node & server version 2.
Now I can't add users. The output is:
> admin@silverlodge:~$ sudo /usr/NX/bin/nxserver --usercheck admin
Password:
NX> 900 Verifying public key authentication for NX user: admin.
NX> 900 Adding public key for user: admin to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: admin.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: admin
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.
Needless to say, 'admin' can log in - I'm logged in as it now! And the ownership & permissions of those files are OK. And I have StrictModes disabled in SSH.
Anyone seen this before, please?

---

### Post by xela321 on 2006-08-19
jkbrowne, your tutorial was fantastic.  You helped me recover from hours of frustration with other tutorials.  You have helped me make the complete switch to linux.  The only thing that was holding me back was finding a replacement to windows' remote desktop.  VNC just doesnt cut it, and freenx was a real pain to set up.  Thanks to you, I can now install kubuntu on my main desktop!

Thanks again!

---

### Post by Camino on 2006-08-19
> **Soarer said:**
> I had the previous version working fine. Removed it all, installed client, node & server version 2.
Now I can't add users. The output is:

Needless to say, 'admin' can log in - I'm logged in as it now! And the ownership & permissions of those files are OK. And I have StrictModes disabled in SSH.
Anyone seen this before, please?

Hey,
I have the same problem. I can´t login in NX and getting the same error if I do a --usercheck

Anyone knows a solution....

Bye

---

### Post by Soarer on 2006-08-19
Well I kinda solved mine, but the solution is a little embarrassing...

I eventually doscovered that I could SSH into the box from outside using its LAN IP Address, but I couldn't SSH on the box itself - i.e. to 'localhost' or 127.0.0.1. Some part of the NX session does SSH to 'localhost' - its in the logfile.

So (this is the embarrassing bit) if I put an entry in the 'hosts' file for localhost, pointing to the LAN IP address, it works. So I can't SSH to 127.0.0.1 probably due to firewall rules (I'm running Shorewall) but I can to 192.168.0.1 (the server's IP address on the LAN.

And it just works, and was never actually an NX problem...

---

### Post by Camino on 2006-08-20
thanks for your answer.

I got this one solved now and the new version is running great

My solution was to modify the server.cfg and node.cfg and enable the ssh_auth_server and the user_db=0 / user_passwd_db=0 in server.cfg. Those were not enabled in the standard installation

Thats it...

Bye

---

### Post by volvoguy on 2006-08-31
> **ethridgt said:**
> Volvoguy, I have your solution.  Well, at least I hope I do.  I was having the exact same problem as you.  This is a version of Ubuntu that I have upgraded since Hoary.  The problem had to do with the font paths.

Whoa. Sorry for seemingly ignoring this ethridgt. I use a Gmail account for all my Ubuntu related communication and "real life" has kept me from being really involved lately.

Your fix sounds like exactly what I need, although with all the *NX frustrations I finally just killed the GUI on the remote machine in question and have been running it headless. I really need to repurpose the machine though, as it's got enough horsepower to do the tasks of several machines on my network. When I do that I'll probably install some sort of GUI just in case I need it (probably a *box window manager or XFCE), in which case I'll want to try the NoMachine stuff again. 

Thanks again!

Aaron

---

### Post by Sara on 2006-09-09
Thanks to jkbrowne for the info on setting up NX Free Server. 

I have an old PC that I have set up as a file/backup server using U```

```buntu Server Kernel and Xubuntu. After getting FreeNx going and finding the compatibility problem with the Client Ver.2.0.0 on Windows, I gave up and set up the NoMachine NX Server. 

The NoMachine documentation for the server and client is very thin, so I hope the following will prevent some loss of hair. If anyone finds some real documentation please let us all know. 

**Client issues**
The client I used is named nxclient-2.0.0-98.exe. It and the installed files do not have any version information so it is a bit confusing. The downloaded client file has a modified date of 7th Sept. 2006. 

I used the fonts files from the NoMachine site instead of loading them from the server. If you want to enable the font server, it can be configured in node.cfg, see below.
I encounter two problems (bugs). 

The installer for the fonts puts them in 
..\NX Client for Windows\X11R6\... 
but the Client software looks for them in 
.....\NX Client for Windows\usr\X11R6\....
This does not impact using a GUI but complete breaks a console window. I manually moved the files to fix this one.

The second problem, which only occurs on XP, and probably Win2000/NT, is that the default 'User NX directory' name can get too long. This is one cause of the error message
Info: getFreeDisplay: path=C:..\.nx/D-Fred-1E053EB44E4F631CE5A544289139385B/.X11-unix/X0
Failed to connect to the X server on [:0]. Error is [2], [No such file or directory].

The work around is to change the User NX directory from the Configure>Environment selection on the Log in window. 

**Server notes.**
For the server there are few issues. The config. and other files are in /usr/NX/etc instead of the usual place.
 
There are a number of settings that are useful in node.cfg.
As I use it on a local LAN I don't use SSL because of the load it puts on the server. This also stops some of the client windows vanishing without explanation found in this and other threads postings:
```
ENABLE_UNENCRYPTED_SESSION = "1"
```
If the server forces encryption, value 0 or default, the client just 'vanishes' without a message when SSL is turned off.

To allow normal Linux user authentication I uncommented:
```
COMMAND_XAUTH = "xauth"
```
To make sure you can get your default windows manager uncomment:
```
DEFAULT_X_SESSION = "/etc/X11/xdm/Xsession"
```

I am sure that there are other setting that are not quite compatible with a standard Ubuntu setup as well, but at least they will probably be in the files in these directory.

The [settings from Fisslefink ]("http://ubuntuforums.org/showthread.php?t=156019&highlight=nx+server")which apply to FreeNX appear to be useful as a guide. 

I hope this has been useful for some of you.
Regards
Sara.

---

### Post by toaster91 on 2006-09-18
Trying out nxclient from Ubuntu for the first time and was getting the error "NX Client Unable to create X authorization cookie" that some others have reported.  

In my case it was due to running Xgl/compiz instead of the regular X server.  It is running on display :1 instead of :0.  When nxclient tries to retrieve the magic cookie for display :1, it isn't found (and 'No matches found, authority file "-" not written' is displayed on the console).  Resulting a failure to connect.  

I was able to work around the problem by running 'xauth list', which returned an entry for my machine 'toaster' on display :0
  toaster/unix:0  MIT-MAGIC-COOKIE-1  XXXXXXXXXXXXXXXXXXXXXXXXXXXXX

I then ran 'xauth add toaster/unix:1  MIT-MAGIC-COOKIE-1  XXXXXXXXXXXXXXXXXXXXXXXXXXXXX", by cut/pasting the long number from the text above and changing the display number.  I now have the same magic cookie for both display :0 and :1.  Retrying nxclient no longer displayed the error.

Unfortunately, still trying to get nxclient working with Xgl (it now connects okay, but fails later in the process), but I thought I'd share this tidbit of info.

---

### Post by hugmenot on 2006-09-18
> **ethridgt said:**
> Volvoguy, I have your solution.  Well, at least I hope I do.  I was having the exact same problem as you.  This is a version of Ubuntu that I have upgraded since Hoary.  The problem had to do with the font paths. 

Check out ~/.nx/<some-unique-directory-name>/status.  Mine had a line that read fatal server error, could not find font 'fixed'.  The unique name is just random letters and numbers.  It creates a new directory each time.

I had to modify /usr/NX/etc/node.cfg.  I added this line:


Tale, you are the chief savior of the day. Damn. For months I kept looking all over the place for clues why some process dies when logging in. Had I known that the clue was in "status"...!
When freenx was still the way to go there was a similar problem with the path to the xauth executable and some RGB variable being unset. I could have known that it had to be something similar. I bow in respect for your analytic and forensic abilities.

---

### Post by makhand on 2006-09-26
ethridgt, Thank you! fixed my problem.

---

### Post by ardnut on 2006-09-29
```
NX> 900 Verifying public key authentication for NX user: admin.
NX> 900 Adding public key for user: admin to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: admin.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: admin
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.
```

After uninstalling freenx and then installing version 2.10 from the nomachine website (the free server they now offer) I also got the above error, but to fix this I had to change my /etc/ssh/sshd_config file.  It still had the line...
```
AuthorizedKeysFile     /var/lib/nxserver/home/.ssh/authorized_keys2
```
Which is  a directory that no longer exists, so I changed that to  
```
AuthorizedKeysFile      /usr/NX/home/nx/.ssh/authorized_keys2
``` restarted ssh (sudo /etc/init.d/ssh restart) and now it works :D

---

### Post by leteci on 2006-10-04
After uninstalling freenx and then installing version 2.10 from the nomachine website I also got the above error

NX> 203 NXSSH running with pid: 964
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.200 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 2.0.0
NX> 134 Accepted protocol: 2.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: borut
NX> 102 Password: *********
NX> 103 Welcome to: borut user: borut
NX> 105 Listsession --user="borut" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-gnome" 
------ ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: borut
" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: B7AB27E1. To get detailed information about
NX> 595 ERROR: the error search for the string B7AB27E1 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
Killed by signal 15.

---

### Post by jonesbeach on 2006-10-05
Leteci,

I was having the same problem.  I read somewhere else that you need the change the ownership of the .Xauthority file from root to user.  The file is located in /home/~/.Xauthority.  This fix worked for me.  Good luck, it was driving me crazy, too!

---

### Post by leteci on 2006-10-05
> **jonesbeach said:**
> change the ownership of the .Xauthority file from root to user.  The file is located in /home/~/.Xauthority.  

it works! thnx

---

### Post by wilpert on 2006-10-18
Hi

I install NX free edition server in ubuntu and everything works fine but i have little problem with my windows nxclient. When i connected to ubuntu and remote screen opens (gnome) i cant see gnome panel at all. So i can see background picture and quicklinks in desktop but not gnome panels (up and down). 

i also installed nxclient in same machine where i run nxserver (ubuntu) when i connect to localhost with ubuntu nxclient everything works fine. I can see also gnome panels :confused: When i terminate or suspend my localhost session and connect with same username but in windows nxclient now everything works fine. :confused:  

So why i have to first connect with linux nxclient before i can see gnome panel in windows nxclient??

can anyone help me ](*,)

---

### Post by hugmenot on 2006-10-19
> **wilpert said:**
> 
can anyone help me ](*,)

It is perhaps that GNOME keeps the panels where they were previously /with respect to XY coordinates/.
Is the screen resolution you use on Windows the same as before? Can you press Alt+F1 to open the Applications menu still?

---

### Post by wilpert on 2006-10-19
> **hugmenot said:**
> It is perhaps that GNOME keeps the panels where they were previously /with respect to XY coordinates/.
Is the screen resolution you use on Windows the same as before? Can you press Alt+F1 to open the Applications menu still?

Hi 

I think that i solve the problem. I have use "full screen" mode in nsclient in windows. Now everything works great. So is the nxserver and nsclient the effectively and safety combination to remotely administrate work computer from home?

---

### Post by hugmenot on 2006-10-19
> **wilpert said:**
> Hi 

I think that i solve the problem. I have use "full screen" mode in nsclient in windows. Now everything works great. So is the nxserver and nsclient the effectively and safety combination to remotely administrate work computer from home?

Yes.

---

### Post by skenliv on 2006-10-22
Just a side note, NXserver does NOT work on the latest Edgy Eft at ALL.
It does not find any of the locations when installed.
All is broken ](*,)

---

### Post by yanokwa on 2006-10-23
This rocks hardcore. Thanks for the instructions! My Mac can now connect to my Ubuntu box.

---

### Post by bupkes on 2006-10-25
My NX installation fails to bring up xterm or any x-terminal-emulator apps.  Otherwise the session starts up normally, my desktop (fluxbox/xdm) appears, and other apps like firefox load normally.

Here's what I did:
installed the server version of Dapper on an old box (Pentium II/192MB RAM)

aptitude install menu fluxbox x-window-system-core xdm xterm (This was suggested as a minimum lightweight system in the ubuntu user docs for low memory systems)

installed nxclient,nxnode,nxserver from nomachines

.xsession only invokes fluxbox  When I tried to add xterm & prior to fluxbox, I got a system beep before fluxbox started.  I get a system beep everytime I try an xterm based app.

I start NX with Unix,Custom, new virtual desktop,/usr/bin/startfluxbox

I do see a "Session:display failure detected" and font not found errors (nil2 and misc fixed medium) in some but not all session files in ~/.nx/[uniquesessionname]

fwiw, default_X_session is commented out in node.cfg as is default_X_WM

Help?

I've googled and read in ubuntu, nx, fluxbox, and x sites and forums.

---

### Post by tritonph on 2006-10-30
I have the same problem... Gnome panels on the top and bottom are not being displayed. Anybody knows how to fix this?

---

### Post by garretwp on 2006-10-30
I can not get nxserver running at all on Edgy. Has anyone else had luck?

- Garrett

---

### Post by 1comment on 2006-11-08
This message is really only for Dgurion and Sweatherly who were having the weird timeout problems after clicking "Yes" to the RSA authenticity question.

I had been having the exact same issue and only tonight was I able to actually solve it without a complete reinstall.  The only things I did were :
  1) Completely uninstall NXclient (registry inspection as well)
  2) Download and install NXclient 2.1.0-9
  3) edit /etc/hosts.allow and add the line "sshd: ALL"
  4) /sbin/service sshd restart

I was then able to get past the timeout issue and connect up normally.

Hope this helps you guys if you've not already fixed the issue.

---

### Post by acegolfer on 2006-11-12
> **garretwp said:**
> I can not get nxserver running at all on Edgy. Has anyone else had luck?

- Garrett

I haven't tried nomachine nx server. But freenx using Dapper repo on Edgy works fine. There's no Edgy repo yet. Give it a try. You will need to use nxclient 1.5 instead of 2.0.

Is there any difference between nomachine nx and freenx?

---

### Post by Asteroza on 2006-11-13
> **garretwp said:**
> I can not get nxserver running at all on Edgy. Has anyone else had luck?

- Garrett
I did a straight install of Edgy, then the 1,2,3 of client, node, and server from the debs at nomachine.com then did the sshd_config addition of the NX server keys as outlined by others here, restarted ssh. Then used the client to localhost port 22 and it worked, first time, after complaining about the fingerprint. I did set for SSL encryption (this forces all activity through one port), and set GNOME for the client before connecting though. This is with the new 2.1 release stuff though, so perhaps some issues have been fixed?

Now, to actually get it working from elsewhere, that's a different issue I have yet to tackle.

On a side note, is there a clean and simple way to hook into an existing GNOME session on the server? Doubling through VNC seems like a waste, and half the reason some people tried NX was to look at their open sessions in a better/safer way than VNC.

---

### Post by hugmenot on 2006-11-14
> **Asteroza said:**
> I did a straight install of Edgy, then the 1,2,3 of client, node, and server from the debs at nomachine.com then did the sshd_config addition of the NX server keys as outlined by others here, restarted ssh. Then used the client to localhost port 22 and it worked, first time, after complaining about the fingerprint. I did set for SSL encryption (this forces all activity through one port), and set GNOME for the client before connecting though. This is with the new 2.1 release stuff though, so perhaps some issues have been fixed?

I think getting the "Free Edition" of !M upand running is really a simple thing in the meantime. Do you even need the sshd_config thing still? For me installing three debs was enough.

> 
Now, to actually get it working from elsewhere, that's a different issue I have yet to tackle. Do you even need the sshd_config thing still? For me installing three debs was enough.

Forwarding is really simple because you only need port 22 open to the outside. (Or another pref. higher port)

> 
On a side note, is there a clean and simple way to hook into an existing GNOME session on the server? Doubling through VNC seems like a waste, and half the reason some people tried NX was to look at their open sessions in a better/safer way than VNC.
There&#8217;s a low priority[ sharing feature]("http://www.nomachine.com/fr/view.php?id=FR10C01069") planned. It will leverage a similar machanism to VNC to monitor desktop changes, so actually using VNC though NX will provide a stop-gap measure.

---

### Post by kanenas on 2006-11-21
I successfully  install the nomachine nxserver,node and client and everything seems to work as expected except one think

my box has 3 accounts the root, the user kanenas and the user remote

i can login with user remote but i can not with user kanenas

using sudo /usr/NX/bin/nxserver --userlist both users are authorized, why is this happening?
please help

---

### Post by volvoguy on 2006-11-22
> **Asteroza said:**
> On a side note, is there a clean and simple way to hook into an existing GNOME session on the server? Doubling through VNC seems like a waste, and half the reason some people tried NX was to look at their open sessions in a better/safer way than VNC.


I'll apologize in advance for the lack of technical info here, but if you have an X server on your client machine, you can forward the display from one machine to the other - at least I'm pretty sure you can do this with the entire desktop. I did it long, long ago and only forwarded individual applications. 

I have a fresh Dapper server install and I'm really missing just a few graphical things that I used to do with it (with the standard desktop install) so I guess I'm going to be looking into X forwarding or freenx/NoMachine again. I'll keep ya'll posted as to my success.

Aaron

---

### Post by AllSystemGo on 2006-11-24
Can anyone help me out with this. I have the NXServer running the ssh Running. Now I connect with my NXClient from my Windows 2K platforme but if I try to start a FireFox on my client and there is someone else using FireFox, whether it's the console itself or another NXClient, it gives me a

```
FireFox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
```

How can I run more then one session of Firefox all at once??

Cheers

---

### Post by dannyboy79 on 2006-11-24
ha, this happned to me also just yesterday. it's only because firefox updated itself and you need to do a ps aux | grep firefox, find out the pid and then do a sudo kill "pidnumberforfirefox" and then you can open fierfox and you should be good to go. it has nothing to do with nxserver. this just happened to me, it's because firefox updated itself, did you notice the light bulb in the upper right corner? i had one anyway. try what I am saying and that should do it.

---

### Post by Macchi on 2006-11-29
> **kanenas said:**
> I successfully  install the nomachine nxserver,node and client and everything seems to work as expected except one think

my box has 3 accounts the root, the user kanenas and the user remote

i can login with user remote but i can not with user kanenas

using sudo /usr/NX/bin/nxserver --userlist both users are authorized, why is this happening?
please help

I believe there is a limit on 2 users for the latest free NX server. It could be something like that. But look also at the SSH server configuration and also group and user privileges that might affect this.

---

### Post by acegolfer on 2006-11-30
I tried to upgrade from FreeNX (1.5) to NoMachine NX (2.1) in Edgy. I was using higher port instead of standard 22. So I've changed port numbers in both node.conf, nxserver.conf. But when I checked the status of nxserver (after restarting), it tries to connect through port 22 and gives error messages. How do I change it? Or, is it really broken as some other claimed in Edgy? 

I'm back to FreeNX.

---

### Post by mip on 2006-12-05
I installed as per instructions but when I do:

```
/usr/NX/bin/nxserver --status
```

I get:

```
NX> 900 Connecting to server ..
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
```

Any suggestions?

---

### Post by cultpenguin on 2006-12-06
> **andersja said:**
> 
```
$ cat session
...
...
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.

Fatal server error:
Error: Unable to open display 'nx/nx,options=/home/username/.nx/C-servername-1004-7F39881E8F0AA7552592ADF4878854E8/options:1004'.

```

My network is just fine; I can successfully ssh to the box from the outside world using putty. My firewall (in my router) blocks all inbound requests bar port 22 and 443.

Hi Anders.
I got the same error message after upgrading to Edgy. When I removed my Xauthority file
rm ~/.Xauthority
the problem went away.

Hope this helps
- Thomas

---

### Post by dannyboy79 on 2006-12-07
> **mip said:**
> I installed as per instructions but when I do:

```
/usr/NX/bin/nxserver --status
```

I get:

```
NX> 900 Connecting to server ..
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
```

Any suggestions?

believe it or not I get this same error but when I use nxclient in winbloz xp I connect just fine so I am not sure why --status fails? i think it may be because the i have my server.cfg and node.cfg using sshd authentification instead of using the nxserver database. do a locate server.cfg and go down the whole file and you can read what options you'd like to toggel on and off. 1 thing I still haven't got working is having nxserver authenticate with a dsa key pair that has a passphrase but it may work if I use a ssh agent like paegent. I am looking into that now. I don't feel comfortable leaving my ssh server with password authentication because with enough time brute force can eventually break all passwords. although with my password, I have puncuation, lower and uppercase letters and numbers and according to a brute force website, it would take a password program over 1 million years to break my 8 letters password that has upper, lower case letters, numbers, and puncuation as well symbols I just remembered. so I would like to turn off password authentification and only count on private/pub key I can't due to nxserver not authenticating then. cause I sure don't want to use a key pair that doesn't have a passphrase cause then if some1 gets there hand on the private key, they'll have access to all my servers and I can't have that. if you have port 22 forwarded in you hardware router, take a look at your /var/log/auth.log and you'll see the attempts to break into your sshd server. every time I get a new ip, I send them an email (i get an abuse email address by using whois iphere), I tell them to stop it or I'll have the FBI shut down there ISP and I tell them if they aren't doing this on purpose that their machine has already been taken over by a hacker. next I add that ip range (usually always from hong kong, china, japan) to drop all connections from that ip in iptables. I just hate haviung to do this. I wonder if I can somehow create a little script that'll read auth.log and if auth.log states blah ip tried and failed to connect then it would just add that ip to iptables and not allow any connections, that would be a cool thing to learn how to create a program to do that. I am trying to learn python, maybe I habe just come up with my first project. sorry for blabbering on and on. see ya

---

### Post by cow_racer on 2006-12-08
I'm trying to install NX from NoMachine on a 64 bit processor.
I downloaded the tar.gz files since Dapper refuses to install the deb (wrong architecture).

sudo /usr/NX/bin/nxserver --status
NX> 900 /usr/NX/bin/nxssh: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
NX> 110 NX Server is stopped.
NX> 999 Bye.


I don't know where I can find libstdc++-libc6

The latest I have is /usr/lib/libstdc++.so.6

---

### Post by kikeboy on 2006-12-09
> **jkbrowne said:**
> Ok, I've fought with this off and on for a-while, but I finally found the right combination.  First of all, forget freeNX.  The NoMachine folks have released a "desktop" edition of their latest product called "NX Desktop Server" that is free for personal use (2 users/connections).  

Before proceeding, be sure to *completely* remove any previous versions of any of the FreeNX files or libraries.  Undo what you have already done, and remove the FreeNX source URLs from your /etc/apt/sources.list.


-----------------------
Step 1 - Download
-----------------------

Download "NX Desktop Server DEB for Linux" from:
[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Download "NX Node DEB for Linux" from:
[http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

Download "NX Client DEB for Linux" from:
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

-----------------------
Step 2 - Install
-----------------------
Install the DEB files in this order:

nxclient
nxnode
nxserver

I just right-clicked on them and installed them...use apt-get if you prefer.

-----------------------
Step 3 - Configure
-----------------------
Load up your /etc/ssh/sshd_config file into an editor:

sudo nano /etc/ssh/sshd_config

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart

Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status

This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration.  If not, then NX Desktop Server should be installed.

Before anyone complains, yes, I'm using the NoMachine server key just because it's easy.  If you want to generate your own key, you can.  These instructions worked for me on Dapper....YMMV.  Let me know if you have trouble.....hopefully my notes were correct.

Good luck!
Hi, I've donde the installation following your instructions, an it works fine, now I like to create my NoMAchine server key in order to have more protection, how can I do this? in other guides suggert nxsetup --install --clean, but I don't know if it is a good idea. can you helpme?

---

### Post by xphelanx on 2006-12-12
I'm running Edgy and I've gone through the whole dealio installing each of the packages from the nomachine.com site in the proper order and everything including editing my sshd_config. I have it working so that I can connect using another computer (windoze) on my home network. However, if I try to connect using my global ip instead of 192.168.2.xxx then it goes through the whole authentication/connection process but seems to hang during the 'Negotiating link parameters' step and the client gives me a msg window saying; "Could not yet establish the connection to the remote proxy. Do you want to terminate the current session? y/n" In the details for the error it gives me this:

Info: Display running with pid '308' and handler '0x2705e4'.
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '344'.
Session: Starting session at 'Tue Dec 12 10:06:13 2006'.
Info: Connecting to remote host '192.168.x.xxx:5018'.
Info: Aborting the procedure due to signal '15'.
Session: Session terminated at 'Tue Dec 12 10:07:12 2006'.

I obviously have my SSH port open on my router.
Can anybody help me out with this? ](*,)

---

### Post by j1979c on 2006-12-16
Followed this guide which lead me to this thread and it totally works 100% for me. :p 

Thanks jkbrowne and jack! :mrgreen: 

[http://michigantelephone.mi.org/blog/2006/09/how-to-install-nx-server-and-client.html](http://michigantelephone.mi.org/blog/2006/09/how-to-install-nx-server-and-client.html)

---

### Post by auslander1138 on 2006-12-18
> **mip said:**
> I installed as per instructions but when I do:

```
/usr/NX/bin/nxserver --status
```

I get:

```
NX> 900 Connecting to server ..
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
```

Any suggestions?

Hi all,

Thanks for the mini-howto, but I am getting the same errors as mip above.

Has anyone found a fix for this?

I'm looking forward to getting this working.

I'm running a fresh install of Edgy Eft x86 and using the latest packages from nomachine.com

Thanks again!

aus

---

### Post by Sweatboy on 2006-12-19
I've got NoMachine's NXServer 2.1.0.13 installed on my Dapper machine. It works great. I'm trying to get the SSH PasswordAuthentication "no" option working with NXServer and haven't had any luck. When this is turned on, the user I'm logging in as doesn't autheticate. I saw a posting for FreeNX on solving this but NoMachine's version of the product doesn't seem to have the same options of ENABLE_SSH_AUTHENTICATION and ENABLE_SU_AUTHETICATION. Any help here would be appreciated.

---

### Post by auslander1138 on 2006-12-20
...well I was finally able to get nomachine's nxserver running on my Edgy box after much tweaking and playing around.

I still get the errors when I do a "sudo /usr/NX/bin/nxserver --status", but clients are able to connect and resume is actually working!

It was something silly on my part anyway--make sure to comment out the original entry for "AuthorizationKeysFile" and just use the one provided by NX

I also generated a new key and imported it to the clients trying to connect and voila!  All is working.

Cheers!

aus

---

### Post by ChM on 2006-12-21
[COLOR="Red"]***** DON'T DO THE SUGGESTED CHANGE TO SSHD_CONFIG *****[/COLOR]

This completely opens your host to remote access ! Any one could login on any of your accounts through ssh.
 
Please apply the following procedure instead:

1° in /etc/ssh/sshd_config 
make sure the following lines are present and all uncommented
> 
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile     %h/.ssh/authorized_keys


It is very important that you leave the %h. This tells sshd to look in the user's home directory for this subdirectory and file. If you modified the file don't forget to restart the ssh server with this call > > /etc/init.d/ssh restart 

2° then go into ~nx/.ssh and there you will see the file authorized_keys2. Obviously this is not the name specified in sshd_config. So remove the '2' at the end of the file name. You could also add a '2' in the configuration file, but I would leave the ubuntu files as they are and simply correct nx. 

What is the problem with the previously proposed change ?

It tells sshd that it should allow automatic login (without password) to any user who has the private key corresponding to the public key of nx. This private key is easily extracted out of nx clients. So the big mistake is to remove the %h from the authorized_key parameter. 

The autorized_key allows nx to login without giving a password. The account is configured so that a connection is immediately attached to an nxserver program that will then ask the user password. I guess this is done to allow nxserver to use its private account database. Your host could have accounts A,B and C accessible through ssh, and you would want that only A can use nxserver. You then have to manage nxserver specific accounts.  

This public-private key usage made by nxserver is the main source of problem for installation. 
Generating its own bi-keys is always safer and would reduce the risk of the error. 
So please broadcast the message and correct the initial post !

---

### Post by dannyboy79 on 2006-12-21
> **auslander1138 said:**
> Hi all,

Thanks for the mini-howto, but I am getting the same errors as mip above.

Has anyone found a fix for this?

I'm looking forward to getting this working.

I'm running a fresh install of Edgy Eft x86 and using the latest packages from nomachine.com

Thanks again!

aus

i get this same error but am still able to connect from outside my local lan just fine. the better thing to do to test it would be to use the client and just type in everything into the client like you're trying to connect to it from outside. so use your external ip etc etc. if it works then you can be sure that'll work when you are out and about and wanna connect. i don't know why the status shows this but I believe it has something to do with authentification, did you try adding a debug parameter to see what exactly the error states? wish I could help more but like I said, I get this same error when I do the status thingyu but am able to connect from within my lan using xubuntu and from outside my lan using winxp client.

---

### Post by dannyboy79 on 2006-12-21
> **ChM said:**
> [COLOR="Red"]***** DON'T DO THE SUGGESTED CHANGE TO SSHD_CONFIG *****[/COLOR]

This completely opens your host to remote access ! Any one could login on any of your accounts through ssh.
 
Please apply the following procedure instead:

1° in /etc/ssh/sshd_config 
make sure the following lines are present and all uncommented


It is very important that you leave the %h. This tells sshd to look in the user's home directory for this subdirectory and file. If you modified the file don't forget to restart the ssh server with this call 

2° then go into ~nx/.ssh and there you will see the file authorized_keys2. Obviously this is not the name specified in sshd_config. So remove the '2' at the end of the file name. You could also add a '2' in the configuration file, but I would leave the ubuntu files as they are and simply correct nx. 

What is the problem with the previously proposed change ?

It tells sshd that it should allow automatic login (without password) to any user who has the private key corresponding to the public key of nx. This private key is easily extracted out of nx clients. So the big mistake is to remove the %h from the authorized_key parameter. 

The autorized_key allows nx to login without giving a password. The account is configured so that a connection is immediately attached to an nxserver program that will then ask the user password. I guess this is done to allow nxserver to use its private account database. Your host could have accounts A,B and C accessible through ssh, and you would want that only A can use nxserver. You then have to manage nxserver specific accounts.  

This public-private key usage made by nxserver is the main source of problem for installation. 
Generating its own bi-keys is always safer and would reduce the risk of the error. 
So please broadcast the message and correct the initial post !

some of your statements not true. "It tells sshd that it should allow automatic login (without password) to any user who has the private key corresponding to the public key of nx." this is only partially true, of course depending how you set up your nxserver to authenticate along with sshd, in order to log in, you need the **username** besides having the passphraseless private key. you can set the nxserver to use pam instead of it's username and password database. this is what I have done. the problem with this program is that you can't use passphrase private/public key pairs because the nxclient doesn't give you a chance to enter it. so if you have your ssh server authenticating using ONLY private/public key which has a passphrase, you could try to tell the nxserver to use these keys tyhat you already are using but when I did that it didn't work. so what I have done is basically made my sshd_config use the 3 things that you stated above, I also made it so that you can't use pam password authentification but have allowed challangepasswordauthentification. not sure what the difference is but for my normal putty, I use a passphrased private key pair and then when I use nxclient, I simoly use my pam username and password to log into my nxserver. i have very smart username and password so it would take some1 about 45 years to brute force them. i wish the nxserver would allow for passphrase private key pairs but it doesn't.

explaination:
ssh can be authenticated several different ways: GSSAPI-based authentica-
     tion, host-based authentication, public key authentication, challenge-re-
     sponse authentication, and password authentication. this is all found in the man pages. i have added a link to it: [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh).

---

### Post by ChM on 2006-12-21
Here is the procedure to generate and use your own bi-keys.

1° First switch user to become nx. Since it would by default start nxserver, we force it is use a bash shell instead. The password request is for the sudo. Then go into .ssh directory. 

> 
> sudo su --shell /bin/bash nx 
> cd ~nx/.ssh
 

2° The following three instructions will generate a new key pair and will add them to the authorized_keys file. Hit the return key when asked for a pass phrase. There should be no pass phrase.  

> 
> ssh-keygen -t dsa -f id_dsa1
> echo -n "no-port-forwarding,no-agent-forwarding,command=\"/usr/NX/bin/nxserver --login\" " >> authorized_keys
> cat id_dsa1.pub >> authorized_keys



3° The file id_dsa1 contains the private key that needs to be given to the nxclient. 
To do this, go to the client configuration display and click on the 'Key' button. Then replace the text field content with the content of the id_dsa1 file. Include the dashed header and trailer in your copy. 

Now go and try it out. If it works you may remove the first line of the authorized_keys which is the initial key we don't use or put a '#' in front of the line which locks out the entry. 

You can copy the private key into the other clients that may connect to the nxserver or you may generate new key pairs. To do so execute the same three instructions above simply changing id_dsa1 into id_dsa2. In this case you can lockout one of the clients by simply adding a '#' in front of the corresponding line. 

If this doesn't work, please check carefully that you correctly typed the file names. Check that the sshd_config file name matches the one you used. Check that you restarted ssh after any changes to the ssh configuration file. Check that ownership of authorized_keys file is nx nx. 

For safeness, check that the private keys are readable only by nx user.

---

### Post by ChM on 2006-12-21
> **dannyboy79 said:**
> ... you need the **username** besides having the passphraseless private key. 

I assumed that the default noMachine key pairs are installed in which case the risk is serious. If new key pairs are generated when installing nxclient, nxnode and nxserver then the risk is much lower indeed. So lets hope my assumption was wrong. 

You are right about the username, but this can be easy to guess. It can be the first or last name of the target, the name in its email address, etc. 

The point is to [COLOR="Red"]not remove the %h in the sshd_config[/COLOR]. It weakens the security or even compromise it and there is no added value that can justify it.

If the private key allows ONLY to connect to nx accounts and thus to nxserver, then the fact that it is passphraseless is not a critical issue since nxserver takes care of the access checking. The problem is if one can connect to other accounts and thus a normal shell with this private key. This is made possible with the initial suggested change to sshd_config file.

---

### Post by dannyboy79 on 2006-12-21
> **ChM said:**
> I assumed that the default noMachine key pairs are installed in which case the risk is serious. If new key pairs are generated when installing nxclient, nxnode and nxserver then the risk is much lower indeed. So lets hope my assumption was wrong. 

You are right about the username, but this can be easy to guess. It can be the first or last name of the target, the name in its email address, etc. 

The point is to [COLOR="Red"]not remove the %h in the sshd_config[/COLOR]. It weakens the security or even compromise it and there is no added value that can justify it.

If the private key allows ONLY to connect to nx accounts and thus to nxserver, then the fact that it is passphraseless is not a critical issue since nxserver takes care of the access checking. The problem is if one can connect to other accounts and thus a normal shell with this private key. This is made possible with the initial suggested change to sshd_config file.

if you're saying that's it easy for some1 to steal a private key from the nxclient than it really is irrelevant whether the public key file (authorized_keys) is stored in the main user's home directory or if it's stored in the nx users home directory does it????? 

"I assumed that the default noMachine key pairs are installed in which case the risk is serious." if the user choses to use the default keys then yes, they are installed by default. "If new key pairs are generated when installing nxclient, nxnode and nxserver then the risk is much lower indeed." WHY???? They are both passphraseless so I don't see why it matters. Plus I don't agree with using a passphraseless key for my ssh server which you're saying you do.  there is a way more secure way to do this than what you are proposing. I mean, you're telling everyone, HEY, DON'T DO IT THE WAY THEY SUGGEST, DO IT MY WAY. but your way is really no different than the way they suggest because they both use passphraseless key pairs.

---

### Post by Jaygo333 on 2007-02-02
> **jkbrowne said:**
> Ok, I've fought with this off and on for a-while, but I finally found the right combination.  First of all, forget freeNX.  The NoMachine folks have released a "desktop" edition of their latest product called "NX Desktop Server" that is free for personal use (2 users/connections).  

Before proceeding, be sure to *completely* remove any previous versions of any of the FreeNX files or libraries.  Undo what you have already done, and remove the FreeNX source URLs from your /etc/apt/sources.list.


-----------------------
Step 1 - Download
-----------------------

Download "NX Desktop Server DEB for Linux" from:
[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Download "NX Node DEB for Linux" from:
[http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

Download "NX Client DEB for Linux" from:
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

-----------------------
Step 2 - Install
-----------------------
Install the DEB files in this order:

nxclient
nxnode
nxserver

I just right-clicked on them and installed them...use apt-get if you prefer.

-----------------------
Step 3 - Configure
-----------------------
Load up your /etc/ssh/sshd_config file into an editor:

sudo nano /etc/ssh/sshd_config

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart

Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status

This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration.  If not, then NX Desktop Server should be installed.

Before anyone complains, yes, I'm using the NoMachine server key just because it's easy.  If you want to generate your own key, you can.  These instructions worked for me on Dapper....YMMV.  Let me know if you have trouble.....hopefully my notes were correct.

Good luck!


Ok, I did all this and all is fine, but now how do I run NXCLient. Tried terminal with nio success. tThe buttons do not appearon top menu so I have no idea how to start them.

---

### Post by Soarer on 2007-02-02
Hi,
Do you not have entries in:

Applications > Internet > NX Client for Linux in the menus?

If not, 'nxclient' on the command line will start it, but I would guess if you don't have those entries you might need to re-install.

---

### Post by TNeloms on 2007-02-18
Thanks, jkbrowne!

I first needed to 'sudo apt-get install ssh' and then your instructions worked perfectly for me.

---

### Post by brdoco on 2007-02-23
Running Edgy.. just removed FreeNX and installed the NX Client/Node/Server deb's following the directions.

When I try to connect from the client machine, I get the error "Server not installed or NX access disabled" with the following details:

```
NX> 203 NXSSH running with pid: 5264
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: xxx.xxx.xxx.xxx on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

(Not sure if this is important, but I'm not trying to connect using the user nx.  I'm trying to connect with my existing system account.)

And for fun, on the server machine..

When I run **nxserver --useradd myusername** i get:

```
NX> 801 User: myusername uses SSHD authentication.
NX> 900 Adding public key for user: myusername to the authorized keys file.
NX> 910 WARNING: The SSH key to be used for user authentication could
NX> 910 WARNING: not be added to the private authorized keys file of user.
NX> 910 WARNING: Please note that, with these settings, the user won't be
NX> 910 WARNING: able to successfully run any sessions.
NX> 910 WARNING: Run the following command to get some hints on the possible
NX> 910 WARNING: reasons of the problem:
NX> 910 WARNING:
NX> 910 WARNING: nxserver --usercheck myusername
NX> 999 Bye.
```


And so when I run **nxserver --usercheck myusername** I get:

```
NX> 900 Verifying public key authentication for NX user: myusername.
NX> 900 Adding public key for user: myusername to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: myusername.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: myusername
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.
```

Any ideas?  I'd appreciate any help.

---

### Post by MeneK on 2007-02-23
I've been running !M free nxserver on a Feisty machine for a couple of days, but now it doesn't work anymore. Every time I try to connect, it displays the black window with the logo for a second and then closes.

```

NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '12477'.
Session: Starting session at 'Fri Feb 23 17:53:41 2007'.
Info: Connecting to remote host '192.168.1.99:5022'.
Info: Connection to remote proxy '192.168.1.99:5022' established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using lan link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-rle-9' with session 'unix-gnome'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '192.168.1.99:5022'.
Info: Listening for font server connections on port '11022'.
Session: Session started at 'Fri Feb 23 17:53:41 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Fri Feb 23 17:53:46 2007'.
Info: End of NX transport requested by remote.
Info: Shutting down the NX transport.
Session: Session terminated at 'Fri Feb 23 17:53:46 2007'.

```

Any idea?
Thanks!

---

### Post by dannyboy79 on 2007-02-23
well did you update your sshd_config file like the install instructions state? are you using the default keys or did you make your own? Did you restart your ssh server? ```
sudo /etc/init.d/ssh restart
```
let me see what the 
AuthorizedKeysFile line within sshd_config states. do ```
cat /etc/ssh/sshd_config
```, then look thru the results until you find a line that starts with AuthorizedKeysFile and post back what the entire line states. If you have 2 of these lines then post them both.

---

### Post by MeneK on 2007-02-23
Voilà:

sudo /etc/init.d/ssh restart
```

 * Restarting OpenBSD Secure Shell server...                             [ OK ] 

```

cat /etc/ssh/sshd_config | grep AuthorizedKeysFile
```

AuthorizedKeysFile      /usr/NX/home/nx/.ssh/authorized_keys2

```

sudo /usr/NX/bin/nxserver --restart
```

NX> 123 Service stopped.
NX> 122 Service started.
NX> 999 Bye.

```

sudo /usr/NX/bin/nxserver --status
```

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

```

Everything seems ok on the server side (the Feisty machine), but I've tried to connect from different machines (Ubuntu & Windows) and the result is the same: after the black window with the !M logo the connection is closed without any error message.

---

### Post by brdoco on 2007-02-23
> **dannyboy79 said:**
> well did you update your sshd_config file like the install instructions state? are you using the default keys or did you make your own? Did you restart your ssh server? ```
sudo /etc/init.d/ssh restart
```
let me see what the 
AuthorizedKeysFile line within sshd_config states. do ```
cat /etc/ssh/sshd_config
```, then look thru the results until you find a line that starts with AuthorizedKeysFile and post back what the entire line states. If you have 2 of these lines then post them both.

In case you're replying to me...

Yes, I've restarted the ssh server and the nx server several times... as well as even rebooted.

For the sshd config file, yes I followed the instructions...

```
RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys
AuthorizedKeysFile      /usr/NX/home/nx/.ssh/authorized_keys2
```

As for the keys, I'm trying to generate my own (at least that's what I thought nxserver --adduser followed by nxserver --checkuser did).  But becasue it can't write to the file, I can't get the key to copy it to my client machine.

---

### Post by dannyboy79 on 2007-02-23
there's your problem. you won't be able to log in if you don't have the proper authentification requirements.

---

### Post by brdoco on 2007-02-23
> **dannyboy79 said:**
> there's your problem. you won't be able to log in if you don't have the proper authentification requirements.

I know that's my problem.  That's why I posted the output from --adduser and --checkuser.  I'm getting errors generating my key, and I don't know why.

---

### Post by dannyboy79 on 2007-02-23
> **MeneK said:**
> Voilà:

sudo /etc/init.d/ssh restart
```

 * Restarting OpenBSD Secure Shell server...                             [ OK ] 

```

cat /etc/ssh/sshd_config | grep AuthorizedKeysFile
```

AuthorizedKeysFile      /usr/NX/home/nx/.ssh/authorized_keys2

```

sudo /usr/NX/bin/nxserver --restart
```

NX> 123 Service stopped.
NX> 122 Service started.
NX> 999 Bye.

```

sudo /usr/NX/bin/nxserver --status
```

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

```

Everything seems ok on the server side (the Feisty machine), but I've tried to connect from different machines (Ubuntu & Windows) and the result is the same: after the black window with the !M logo the connection is closed without any error message.

please post your /etc/ssh/sshd_config file. also, you did make sure that if you created your own key that you made it without a passphrase correct?? because the nxclient doesn't allow you a chance to enter a passphrase for a key, it only allows a password prompt which is for either password authentification or it allows for challangeresponse authentification. Your ssh server is the backend of nxserver. so you can't think that you can have a key for your ssh server that has a passphrase and then a differnet key for your nxserver which doesn't have a passphrase, this won't work. Also, is your nxserver authenticating using pam or it's own nx user database, that's another thing people get hung up on. I am using the pam database. meaning i just log into my nxserver using my normal username instead of the nx user crap. here are the important parts of my /usr/NX/etc/server.cfg file:

# If the NX user DB is disabled, any user providing a valid password
# from local DB or through SSHD authentication, can connect to the NX
# system. This is likely to be the default when SSHD authentication
# with PAM is enabled.
#
ENABLE_USER_DB = "0"

# Enable or disable NX password DB:
#
# 1: Enabled. Use NX password DB to authenticate users.
#
# 0: Disabled. Use SSHD + PAM authentication.
#
# System administrators can enable a restricted set of users to con-
# nect to the NX server by setting ENABLE_USER_DB to 1 and adding
# those users to the DB. If user is enabled to connect, his/her pass-
# word will be verified against the current PAM settings by the SSHD
# daemon.
#
# If both 'ENABLE_USER_DB' and 'ENABLE_PASSWORD_DB' are set to 0, any
# user being authenticated by SSHD account will be enabled to connect
# to the system.
#
ENABLE_PASSWORD_DB = "0"


SSH_AUTHORIZED_KEYS = "%h/.ssh/authorized_keys"

this above only says this because I use my ssh server's authorized_keys file, I don't use nx's. so it's referencing the one in my home directory just like the sshd_config is originally because I don't want to use the default key so I made my own. that was everything important that I changed in the server.cfg file. (above)

this is the important line within the node.cfg file:

SSH_AUTHORIZED_KEYS = "%h/.ssh/authorized_keys"

this BELOW is the important part of my sshd_config. I normally like to use keys, but since I would never create a blank passphrase key, I setup my ssh server to accept challengeresponseauthentification

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes
UsePAM yes


# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

so the way my ssh server works is that it first needs a public key to be able to work, when I use putty I have a key to it asks me for my passphrase and I am let into my ssh server but when a client doesnt provide a key to the server, (the nx client tool)  the server brings up a password box. this is then the password I use to log into my machine since the name I am using in my nx client is my computer username and the ssh server (which is the backend of the nxserver) is using ChallengeResponseAuthentication. so that's the way I do mine. I would never incorporate a passphraseless key for something as secure as my ssh server. I also only allow certain users to log into my ssh server which is done by 
allowusers xxxxxxxx    (you can add as many users as you want here, just use spaces)

then the other thing to be even more secure is to only allow certain ip's but I don't use that since I don't know where i'll want to access my ssh server from. I rarely use nx client anymore, except when I want to do something on my home mchaine that requires a gui, otherwise I have learned to do a lot within a terminal thru ssh. i sometimes will start up a torrent thru nxclient after I am surfing at work and see that a new torrent was released, this way maybe by the time I get home, it'll be done. yeah! good luck

there's a great thread about it here: [http://www.nabble.com/keyboard-interactive-only-authentication-t1194655.html](http://www.nabble.com/keyboard-interactive-only-authentication-t1194655.html)

---

### Post by dannyboy79 on 2007-02-23
> **brdoco said:**
> I know that's my problem.  That's why I posted the output from --adduser and --checkuser.  I'm getting errors generating my key, and I don't know why.

well there's your problem again. you need to either be using the user nx to log into the server or read my post to the other person. I am not sure how to add users to the nx server password user database sorry.

---

### Post by brdoco on 2007-02-23
> **dannyboy79 said:**
> well there's your problem again. you need to either be using the user nx to log into the server or read my post to the other person. I am not sure how to add users to the nx server password user database sorry.

I understand..

going with your approach, I get the following error when trying to start the nxserver:
NX> 500 ERROR: Cannot link '/usr/NX/home/nx/.ssh/default.id_dsa.pub' to '': /usr/NX/home/nx/.ssh/%h/.ssh/authorized_keys.

---

### Post by dannyboy79 on 2007-02-23
my fault, it's because I told you to put %h/.ssh/authorized_keys for this line:
SSH_AUTHORIZED_KEYS = "%h/.ssh/authorized_keys"

within your server.cfg when it should only just be this:

SSH_AUTHORIZED_KEYS = "authorized_keys"

now how did you create your keys, did you just use ssh-keygen -t dsa? or did you use nxserver tool for creating keys? I just use the ssh-keygen. here is a good guide: [http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html](http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html)

use protocol 2 but you don't need to have your authorized_keys file have the '2' on the end. the name of the irrelevant as long as they all jive in each place the name is called out.

---

### Post by MeneK on 2007-02-23
Thanks for your prompt answer dannyboy79, I will check the ssh config later. But, are you sure that it is an authentication problem? I can see "Authentication Completed" on the client side, and even the big !M logo (see attachments). And it was working just some days ago...

I'm afraid that one the recent Feisty's updates could have broken something.

Thanks again!

---

### Post by dannyboy79 on 2007-02-23
> **MeneK said:**
> Thanks for your prompt answer dannyboy79, I will check the ssh config later. But, are you sure that it is an authentication problem? I can see "Authentication Completed" on the client side, and even the big !M logo (see attachments). And it was working just some days ago...

I'm afraid that one the recent Feisty's updates could have broken something.

Thanks again!

well I can't say for sure obviously but I am guessing. are you using password authentification or key authentification? if key authentification, does your key have a passphrase? if it's got a passphrase than that's why, what's happening is that it connects originally to the ssh server, but then since there is no prompt available to enter your passphrase then nxclient just ends. can you see anything in any log files? /var/log/syslog, messages, or is there any log files that the client creates? gotta go for now. talk with ya later.

---

### Post by hvinther on 2007-02-24
> **MeneK said:**
> Thanks for your prompt answer dannyboy79, I will check the ssh config later. But, are you sure that it is an authentication problem? I can see "Authentication Completed" on the client side, and even the big !M logo (see attachments). And it was working just some days ago...

I'm afraid that one the recent Feisty's updates could have broken something.

Thanks again!

I have the same problem, and my setting all seems to bee identical to the the settings that works on a dapper box, and used to work for me on edgy. So I guess your right, something is broken in feisty now!

---

### Post by hvinther on 2007-02-24
> **hvinther said:**
> I have the same problem, and my setting all seems to bee identical to the the settings that works on a dapper box, and used to work for me on edgy. So I guess your right, something is broken in feisty now!

Here are the lines i get in /var/log/syslog on the server:

Feb 24 09:52:31 medion NXSERVER 2.1.0-18[5217]: User 'joe' logged in from '192.168.1.33'. 'NXLogin::set'
Feb 24 09:52:31 medion NXSERVER 2.1.0-18[5217]: Selected node host:localhost with port:22 'main::selectNode'
Feb 24 09:52:31 medion NXSERVER 2.1.0-18[5217]: Current selected node: localhost is in status: running  'main::selectNode'
Feb 24 09:52:33 medion NXSERVER 2.1.0-18[5217]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Feb 24 09:52:37 medion NXSERVER 2.1.0-18[5217]: Session 'B624A631114F47F2E65CDBFC38F1B9D8' started by user 'joe'. 'NXShell::handler_session_start'
Feb 24 09:52:37 medion NXSERVER 2.1.0-18[5217]: ERROR: run command: no child process with pid 5229 Logger::log nxserver 3591
Feb 24 09:52:37 medion NXSERVER 2.1.0-18[5217]: User 'joe' from '192.168.1.33' logged out. 'NXLogin::reset'
Feb 24 09:52:38 medion NXNODE 2.1.0-15[5236]: INFO: Using port '1014' on node 'medion' for session 'unix-kde'. 'main:nxnode:5551'
Feb 24 09:52:38 medion NXNODE 2.1.0-15[5236]: INFO: Using host from available host list: '192.168.1.37'. 'main:nxnode:5552'
Feb 24 09:52:40 medion NXNODE 2.1.0-15[5256]: ERROR: Failed to set xpi value in command xrdb: /bin/bash -c 'exec -a - /bin/bash -c '\''xrdb -merge'\'': output was: xrdb: No such file or directory\nxrdb: Can't open display 'unix:1014'\n, exit value: 1 'main:nxnode:3664'
Feb 24 09:52:50 medion NXNODE 2.1.0-15[5236]: INFO: Session 'unix-kde' on port '1014' closed. 'main:nxnode:5780'
Feb 24 09:52:52 medion NXSERVER 2.1.0-18[5252]: Session 'B624A631114F47F2E65CDBFC38F1B9D8' closed by user 'joe'. 'NXShell::Static'

---

### Post by lostknight on 2007-02-25
Count me in as another use affected by this. Trying to debug it right now, but no luck so far.
:confused:

---

### Post by brdoco on 2007-02-27
> **dannyboy79 said:**
> my fault, it's because I told you to put %h/.ssh/authorized_keys for this line:
SSH_AUTHORIZED_KEYS = "%h/.ssh/authorized_keys"

within your server.cfg when it should only just be this:

SSH_AUTHORIZED_KEYS = "authorized_keys"

now how did you create your keys, did you just use ssh-keygen -t dsa? or did you use nxserver tool for creating keys? I just use the ssh-keygen. here is a good guide: [http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html](http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html)

use protocol 2 but you don't need to have your authorized_keys file have the '2' on the end. the name of the irrelevant as long as they all jive in each place the name is called out.

Ok, I followed that guide and where's what I get when I just try to ssh into my ubuntu from the remote machine.

On the remote machine, I added the cat'ed id_dsa into authorized_keys2, as the guide said to do.  When that didn't work, I also copied id_dsa and id_dsa.pub into the .ssh directory on the remote machine to see if that would help things... but it didn't.


```

[caesar:~/.ssh] bdc% ssh -2 -v me@myip.org
OpenSSH_4.2p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to myip.org [###.###.###.###] port 22.
debug1: Connection established.
debug1: identity file /Users/bdc/.ssh/id_rsa type -1
debug1: identity file /Users/bdc/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'myip.org' is known and matches the RSA host key.
debug1: Found key in /Users/bdc/.ssh/known_hosts:10
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/bdc/.ssh/id_rsa
debug1: Offering public key: /Users/bdc/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by dannyboy79 on 2007-02-27
according to your debug info, you have 
id_rsa type -1
and
id_dsa type 2
which you really shouldn't have both. although 1 of them should've worked if you copied one of the .pub files into your authorized_keys2 file that should be located within your %h/.ssh/ directory. let me see your /etc/ssh/sshd_config file? you really should be using a different thread as this is for nxserver. there are other threads for ssh server but I'll see if I can help since the nxserver uses the ssh server as it's tunnel.
i also see that it is checking against your private keys that are stored within  the Users folder according to this:
debug1: identity file /Users/bdc/.ssh/id_rsa type -1
debug1: identity file /Users/bdc/.ssh/id_dsa type 2

it should be using the pricate key that you stored within your usernames .ssh directory.
one more thing, I think you have it backward, you need to copy the .pub file into the authorized_keys2 file, then take the private key with you and put on remote machines. that's how I understand it anyway. you can man ssh, see this per the man page:
The
     client uses his private key, ~/.ssh/id_dsa or ~/.ssh/id_rsa, to sign the
     session identifier and sends the result to the server.  The server checks
     whether the matching public key is listed in ~/.ssh/authorized_keys

so that says that the pub key is put into the authorized_keys or authorized_keys2 file (name doesn't matter as long as your sshd_config calls for the correct one) on the server side and you take the private key with you to use on the remote computers.

---

### Post by orstig on 2007-03-09
Hello, i'm running Edgy in a xen domU and the only access is throu nxserver or ssh, my question is how much of the xorg can i remove and how will this work when doning software upgrades ?

---

### Post by dannyboy79 on 2007-03-09
> **orstig said:**
> Hello, i'm running Edgy in a xen domU and the only access is throu nxserver or ssh, my question is how much of the xorg can i remove and how will this work when doning software upgrades ?

this sounds to me liek a question more related to xen or virualization software, which I can't help with.

---

### Post by hvinther on 2007-03-12
> **hvinther said:**
> Here are the lines i get in /var/log/syslog on the server:

Feb 24 09:52:31 medion NXSERVER 2.1.0-18[5217]: User 'joe' logged in from '192.168.1.33'. 'NXLogin::set'
Feb 24 09:52:31 medion NXSERVER 2.1.0-18[5217]: Selected node host:localhost with port:22 'main::selectNode'
Feb 24 09:52:31 medion NXSERVER 2.1.0-18[5217]: Current selected node: localhost is in status: running  'main::selectNode'
Feb 24 09:52:33 medion NXSERVER 2.1.0-18[5217]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Feb 24 09:52:37 medion NXSERVER 2.1.0-18[5217]: Session 'B624A631114F47F2E65CDBFC38F1B9D8' started by user 'joe'. 'NXShell::handler_session_start'
Feb 24 09:52:37 medion NXSERVER 2.1.0-18[5217]: ERROR: run command: no child process with pid 5229 Logger::log nxserver 3591
Feb 24 09:52:37 medion NXSERVER 2.1.0-18[5217]: User 'joe' from '192.168.1.33' logged out. 'NXLogin::reset'
Feb 24 09:52:38 medion NXNODE 2.1.0-15[5236]: INFO: Using port '1014' on node 'medion' for session 'unix-kde'. 'main:nxnode:5551'
Feb 24 09:52:38 medion NXNODE 2.1.0-15[5236]: INFO: Using host from available host list: '192.168.1.37'. 'main:nxnode:5552'
Feb 24 09:52:40 medion NXNODE 2.1.0-15[5256]: ERROR: Failed to set xpi value in command xrdb: /bin/bash -c 'exec -a - /bin/bash -c '\''xrdb -merge'\'': output was: xrdb: No such file or directory\nxrdb: Can't open display 'unix:1014'\n, exit value: 1 'main:nxnode:3664'
Feb 24 09:52:50 medion NXNODE 2.1.0-15[5236]: INFO: Session 'unix-kde' on port '1014' closed. 'main:nxnode:5780'
Feb 24 09:52:52 medion NXSERVER 2.1.0-18[5252]: Session 'B624A631114F47F2E65CDBFC38F1B9D8' closed by user 'joe'. 'NXShell::Static'

It seems this can be helped by adding 'unix' to the host file in same line as 'localhost'. 

[http://ubuntuforums.org/showthread.php?t=375279]("http://ubuntuforums.org/showthread.php?t=375279")

---

### Post by dannyboy79 on 2007-03-12
yes, so that you don't have to click on the link and read it, this is what you need to do. use your favorite editor and open /etc/hosts file, look for the very first line (well it's the first line in mine) make it look like this:

127.0.0.1       localhost unix

this is merely an alias, just like you can have alias's for your hostname, you can have alias's for your loopback.
the hosts file syntax is "Ip address (space or tab) fully qualified domain name (space or tab) alias1 (space or tab) alias2"
IP_address myhost.example.org aliases

NOTE: some programs don't act correctly if you don't have a fqdn, that's when I went to [www.dyndns.com](www.dyndns.com) and got one because sendmail was acting weird and I kept seeing errors in log files.

example:
127.0.0.1 localhost unix
192.168.1.7 yoyo.thisismydomain.com yoyo

---

### Post by MeneK on 2007-03-18
Thanks both, dannyboy79 and hvinther. My nxserver is working again.

---

### Post by forgeuk on 2007-03-28
Anyone help me out with getting this going, followed the instructions, and got the OK from the NX server to say its up and running, but when I try to get into it from work (via internet) it goes through all the process of connecting, authenticates, then stops on the "link parameters" stage with :
aborting the procedure due to signal 15

SSH is working fine, I can get into my PC using PUTTY. Have I set it correctly on the router?
The server is listening on port 22, but my router is set up to allow connections on port 3391 and route them to my pc on 192.168.1.10 port 22 
To me this sounds right, as it is connecting and authenticating, but stumbing at the last bit.
any ideas as VNC just sucks too much.

---

### Post by dannyboy79 on 2007-03-28
are you using public/private keys as your authentification for your ssh server? if so, than this is the problem! there is no way to tell the nxclient to use a public/private key, it can only authenticate using a password. So what I have done is to allow ChallengeResponseAuthentication within your /etc/ssh/sshd_config file. then when the nxclient starts to authenticate, the ssh server will first only authenticate per the public/private if there is one but since nxclient can't authenticate this way, then the ssh server will go to the next acceptable auth method, which is ChallengeResponseAuthentication and then it should accept the password you entered and you should get in. you can fix this thru putty while at work. just don't forget to do /etc/init.d/ssh restart. then putty will fail because you restarted your ssh server but then your nxclient should work! good luck

---

### Post by forgeuk on 2007-03-28
Thanks for your reply DannyBoy.

I've made the alterations you suggested to the config file and restarted the ssh...incidentally, I was expecting to get thrown off when I did reset it, but I didn't, I got the message that the ssh server had been restarted, but stayed connected, so I diconnected, and tried NX again, but the same fault, fails when "Negosiating link parameters".

It connects over the internet, authenticates, then stops with the "link parameters" message, clicking "details" shows this:

Info: Connecting to remote host '192.168.1.10:5018'.
Info: Aborting the procedure due to signal '15'.
Error: Couldn't kill the dialog process with pid '10336'.

One other thing, if I change NX connection to use VNC instead of Unix / Gnome, it doesn't connect at all, but the real VNC client connects every time.

---

### Post by dannyboy79 on 2007-03-28
you didn't answer my question, are you using private/public auth or are you using password auth for your ssh server? r you trying to log into the nxserver with nx as the user or your username for your linux box? if the later did you update your node.cfg and your server.cfg files to reflect this? are you running edgy or dapper? have you rad a few posts back how other users got their edgy to work with nxserver?

---

### Post by forgeuk on 2007-03-29
I wasn't entirely sure what you meant there, when I first connected to my PC using Putty, It said something about a private key, I just clicked ok and it let me in, not seen that message since. On the NX client, there is a default private key in the "key" button. But the login I use is my username/password that I use for both logging in locally and for ssh, so I presumed this is what I should be using to login via NX.

I played around with it locally last night, installed NXclient on another PC on my home LAN, and got in straight away, just tried it from work this morning, and still no go. To me that sounds like a router issue...I'm confused :confused:  As mentioned yesterday, I have setup TCP port 3391 to go to the target PC's port 22, which does work fine for ssh. Does it use any other port? I didn't want to use port 22 externally, seems like a big invite for hackers :-)

I didn't see anything in the node.cfg or server.cfg that I understood, so left them alone. I'm running Edgy and fully up-to-date. I did skim through the previous 11 pages of posts to this thread, maybe I should have a more comprehensive read :)

---

### Post by dannyboy79 on 2007-03-29
it's possible that your work blocks outgoing traffic on that port! try the standard port and see what happens. Also, you could ssh into your box and then run a nmap on your works external ip address to see what ports are open. this will tell you if port 3391 is even open but I doubt it is. most likely 22 is though as this is a standard port (obviously). you'll need to find out your works external ip though, not the internal one! this link can tell what it is ([http://www.ipchicken.com/](http://www.ipchicken.com/)) good luck.

example of nmap scanning port 3391 is:
**sudo nmap -p3391 [www.gogle.com](www.gogle.com)**

or to just see all open ports and is able to get around routers with built in firewalls not allowing pinging:
**sudo nmap -PS -PA [www.gogle.com](www.gogle.com)**

just check out the man page for some more help, it's readable as some of the man pages are way over my head but this one you can pick some great info from it for nmap. (man nmap)

---

### Post by forgeuk on 2007-03-29
Thanks for that info on nmap, thats a neat util, it showed port 22 and 3391 as "filtered" on my work's external IP, so I guess thats not helpful. Anyway, I'll have a read of the MANual and keep playing.

---

### Post by dannyboy79 on 2007-03-29
well, the only way you'll be able to get "out" of your work network is using a port that is open, most likely ports 80 or 25 should be open for web browsing and sending email. so the onyl reall way this can work for you is to map your router port 80 or 25 to the port your ssh server is running on. this will then render the normal services on these ports useless since they are mapped to the ssh port. so if somehow you can set up your home router so that you have remote management of it, you can just log into your router from work, then simply forward the correct port, then do your remote desktop stuff or whathave you. you won't be able to surf the internet or send mail depening which port you ahave forwarded since it's socket will be used by your ssh server, than shut down your nxclient session, log back into your router and unset those forwarded ports and then you'll be able to surf internet again or send mail thru those ports again. or you can always try to look for any other open ports at you work by simply running

sudo nmap -P0 -PA -PS [www.gogle.com](www.gogle.com)

this will look for ALL open ports. this is a link for how people get around work firewalls so that they ssh or vnc into their home boxes. good luck ([http://www.tfproject.org/tfp/archive/index.php/t-57957.html](http://www.tfproject.org/tfp/archive/index.php/t-57957.html))

---

### Post by forgeuk on 2007-03-30
Fixed !!!! - YAY! :guitar: 

I'm still not sure why, but I went and connected again and I got the usual error, then after a few seconds it came up with something different suggesting that I switch on "Use SSL for all traffic" in the client settings, done that and tried again, and I'm straight in. Must be something to do with our Chinese-govenment style firewall we have at work.

Thanks for your assitance and for mentioning nmap.

---

### Post by dannyboy79 on 2007-03-30
yeah, the firewall ports are filtered meaning they probably only allow encryted data thru them since once you checked ssl it started working. glad you are up and running!!

---

### Post by dyerucf on 2007-05-01
Wow, I have been using differnt guides for ever to try and get this working and they all SUCK.  First try with yours and I am up and running this is GREAT.  Thanx


Now to move on the VPN

Thanx  a ton

---

### Post by Dorado on 2007-05-10
> **andersja said:**
> Some additional information - when I go to my ~/.nx directory, I find a subdirectory per failed session. Opening it, I find:

```
$ cat session
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

NXAGENT - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid '32713'.
Session: Starting session at 'Wed Aug  9 10:35:12 2006'.
Info: Proxy running in server mode with pid '32713'.
Info: Waiting for connection from '192.168.1.101' on port '5004'.
Info: Accepted connection from '192.168.1.101' with port '55695'.
Info: Connection with remote proxy established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using isdn link parameters 384/24/1/0.
Info: Using agent parameters 5000/50/0/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/1536/192.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-5' with session 'unix-gnome'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 6/6/32.
Info: Using ZLIB stream compression 9/9.
Info: No suitable cache file found.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.

Fatal server error:
Error: Unable to open display 'nx/nx,options=/home/username/.nx/C-servername-1004-7F39881E8F0AA7552592ADF4878854E8/options:1004'.

```

My network is just fine; I can successfully ssh to the box from the outside world using putty. My firewall (in my router) blocks all inbound requests bar port 22 and 443.

> **cultpenguin said:**
> Hi Anders.
I got the same error message after upgrading to Edgy. When I removed my Xauthority file
rm ~/.Xauthority
the problem went away.

Hope this helps
- Thomas

Help!

I am having a similar problem as described by Andersja above. I tried removing the .Xauthority file as suggested by by cultpinguin but that did not help.

NXserver is running and working fine, I can connect to it perfectly fine another Linux box on my Local network. However when attempting to connect to the server from a my local windows desktop it authenticates & connects but then immediately it bombs out with the "Unable to open display" error. 

Windows seems to have a problem resolving the display, whereas Linux does not. I have tried all the the differnt display options in the client setup... but to no avail.

Has anybody found a solution for this?

Cheers,

Tim

---

### Post by dannyboy79 on 2007-05-10
and which desktop are you chosing in the client, XFCE, KDE, or Gnome?

I have found this using gogle, see if it works for ya.

I found the solution. I did set in node.conf initially this parameter 
ENABLE_2_0_0_BACKEND="1". Removing this parameter was the solution.
I needed to set the parameter ENABLE_1_5_0_BACKEND="1" when I was configuring 
the SUSE Linux 10.1 system, so I assumed this one was needed because I have a 
2.1 NX client.

OR
try this out:
ln -s /usr/share/fonts /usr/X11R6/lib/X11/fonts 
ln -s /usr/share/X11/xkb /usr/X11R6/lib/X11/xkb 
ln -s /usr/share/X11/rgb.txt /usr/X11R6/lib/X11/rgb.txt

because if you view the log files, it's unable to open the display because it can't find the rgb.txt file and or some fonts. at least that's what a ton of other users hve posted.

---

### Post by Dorado on 2007-05-10
Thanks Dannyboy,

I am at work now, so will have to try when I get home. I am using KDE desktop on all my linux boxes and have been selecting KDE in the client.

Will try the node edit and create the links and see what happens.

Cheers,

Tim

---

### Post by Dorado on 2007-05-10
Another look at the seesion log shows that it is slightly different to what Andersja posted:


> 
# cat session

NXAGENT - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '12310'.
Session: Starting session at 'Wed May  9 21:32:30 2007'.
Info: Proxy running in server mode with pid '12310'.
Info: Waiting for connection from '127.0.0.1' on port '5014'.
Info: Accepted connection from '127.0.0.1' with port '46511'.
Info: Connection with remote proxy established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using lan link parameters 1536/24/1/0.
Info: Using agent parameters 5000/50/0/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-rle-9' with session 'unix-kde'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Forwarding font server connections to port '/tmp/.font-unix/fs7100'.

Fatal server error:
Error: Unable to open display 'nx/nx,options=/home/User/.nx/C-localhost.localdomain-1014-A22BDECF04D46CCCB68A0897204E647C/options:1014'.


I am not getting the RGB_DB error.. Perhaps a different problem with same result..."Unable to open display"

I checked the node.conf, the ENABLE_2_0_0_BACKEND="1" line is not present. Neither is the ENABLE_1_5_0_BACKEND="1" line BTW.
I created the links listed below but they do not help either.

Strange that I am able to login to the server from a linux box without a problem....

Scratching my head,

Tim

---

### Post by Dorado on 2007-05-10
Additionally this is the windows client log:

> Info: Display running with pid '3608' and handler '0x30354'.
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '2660'.
Session: Starting session at 'Thu May 10 18:13:51 2007'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using lan link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-rle-9' with session 'unix-kde'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Listening for font server connections on port '11016'.
Session: Session started at 'Thu May 10 18:13:51 2007'.
Error: Failure reading from the peer proxy.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Session terminated at 'Thu May 10 18:13:51 2007'.

Again not much help....

---

### Post by Dorado on 2007-05-10
Mmmm,

Going through all the window log files I found this in the windows error log:

> Loop: WARNING! Disabling NX delta compression.
Loop: WARNING! Disabling use of NX persistent cache.
Proxy: WARNING! Failure detected while trying to handle a partial message for proxy FD#8.
Proxy: PANIC! Failure reading from the peer proxy on FD#8.
Loop: PANIC! No shutdown of proxy link performed by remote proxy.

I am pretty clueless as to what this means....


Hope this means something to somebody?

Cheers,

Tim

---

### Post by dannyboy79 on 2007-05-10
i have read that he 1.5.1 client for windows has had better success.

---

### Post by stoneattic on 2007-05-11
What key should I be using in the client?  

thx

---

### Post by dannyboy79 on 2007-05-12
what do you mean what key? when you installed the server did you tell it to use the default key or did you tell it you'd make your own? if you chose the default key that's very insecure as other's have the same key so if they knew your ip address and you allow outside ip's to connect than they could log into your nxserver. if you chose the default the key should alreeady be in the client. if you choose to create your own you need to make sure you don't have a passphrase as nxclient doesn't give you an opportunity to enter it. you can also not even use key authentification which is insecure as well but is the easiest to set up. just change your /etc/ssh/sshd_config to be password authentification and you should be able to log into your nxserver just using the nx as the user andf whatever passowrd you chose for that user. if you made your own key, well than that's the key you need to use.

---

### Post by stoneattic on 2007-05-12
> **dannyboy79 said:**
> what do you mean what key? when you installed the server did you tell it to use the default key or did you tell it you'd make your own? if you chose the default key that's very insecure as other's have the same key so if they knew your ip address and you allow outside ip's to connect than they could log into your nxserver. if you chose the default the key should alreeady be in the client. if you choose to create your own you need to make sure you don't have a passphrase as nxclient doesn't give you an opportunity to enter it. you can also not even use key authentification which is insecure as well but is the easiest to set up. just change your /etc/ssh/sshd_config to be password authentification and you should be able to log into your nxserver just using the nx as the user andf whatever passowrd you chose for that user. if you made your own key, well than that's the key you need to use.

That was the point of my question I guess.    :)

I'm pretty much lost regarding these keys by now.  

When I installed NXserver I didn't do anything special regarding keys.  I changed sshd_config by adding 
```
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2
```

as suggested on the first page of this thread.  I assume this is using the default key.  I can ssh my way in with out any trouble but NXclient gives authentication errors.  I had NXserver generate a key to try that and copied that to the client but I get the same errors.   I don't follow the whole paraphrase thing.  

I tried changing to password auth just to see if I could connect, figuring if that worked I start messing with the keys again knowing that the keys were the problem, but if I set

```
PasswordAuthentication yes
```

in sshd_config, and restart ssh, then restart NXserver then check the NXserver status and it's stopped.  Is there something I need to change in the server or node configs to use password auth?

Also, I'm using a different port besides 22.  I changed the port in ssh and node.  Is that all I need to do?  I tried to change the port in server but it gives a message about not doing it there, but to do it in node, which I already did.

What other settings should I have on sshd_config?  Does it hurt to have others like:

```

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys2
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2
```

Thanks!

---

### Post by dannyboy79 on 2007-05-12
well i think you  should read abou ssh and how i works. but I can summarize it. you either do password auth or public/priv key pairs which can have passphrases or not. it's more secure to have a passphrase in case some1 gets their hands on your key, than if you have a passphrase then they still can't get in since they'd need to know the passphrase to get in. if you turned on password auth, then you need to change these settings:

RSAAuthentication no
PubkeyAuthentication no

also, I have noticed that if you get a failure when you do nxserver --status I have still been able to log in remotely so I am not sure what that's all about. this is what I suggest. at least get password auth working with nxserver and your ssh server. wha I did was change the nxserver, nxnode so that instead of using the nx database and nx user, I changed it to use pam which is how you authenticate everything on your machine. this is what I did. i have to be honest, I never could get it to work with a custom made key so I am very confident in my password, it's very smart. BUT, i actually don't even use nxserver anymore, I have become pretty good from the cli and can do most of my server admin thru ssh so I went back to key pair auth. good luck

---

### Post by Dorado on 2007-05-12
> **Dorado said:**
> Mmmm,

Going through all the window log files I found this in the windows error log:



I am pretty clueless as to what this means....


Hope this means something to somebody?

Cheers,

Tim


As a last ditch effort I uninstalled and reinstalled the server.

The result is that I now can not even connect to the server from my Linux machine any more

> NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '3751'.
Session: Starting session at 'Sat May 12 19:35:38 2007'.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Sat May 12 19:35:43 2007'.
Session: Session terminated at 'Sat May 12 19:35:43 2007'.


Interestingly enopugh I have no problems connecting to the Nomachine KDE test site from the server machine and from the client machine....

Perhaps it's time to revert back to VNC....


Tim

---

### Post by thk on 2007-05-13
I get this in my auth.log on edgy. Anyone else seen this?

```
May 13 09:41:33 minor nxnode: unable to dlopen /usr/lib/sasl2/libdigestmd5.so.2: /usr/lib/sasl2/libdigestmd5.so.2: symbol DES_cbc_encrypt, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
May 13 09:41:33 minor nxnode: unable to dlopen /usr/lib/sasl2/libntlm.so.2: /usr/lib/sasl2/libntlm.so.2: symbol MD4, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
May 13 09:42:06 minor sshd[5093]: (pam_unix) session closed for user nx

```

---

### Post by mikes86 on 2007-05-14
I'm having trouble getting it to work. When connecting to my server the client fails with,

"The remote proxy closed the connection while negotiating the session. This may be due to the wrong authentication credentials passed to the server."

The log says

Info: Display running with pid '2668' and handler '0x6a049a'.
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '2672'.
Session: Starting session at 'Mon May 14 11:55:42 2007'.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Mon May 14 11:56:01 2007'.
Session: Session terminated at 'Mon May 14 11:56:01 2007'.

---

### Post by stoneattic on 2007-05-15
> **dannyboy79 said:**
> well i think you  should read abou ssh and how i works. but I can summarize it. you either do password auth or public/priv key pairs which can have passphrases or not. it's more secure to have a passphrase in case some1 gets their hands on your key, than if you have a passphrase then they still can't get in since they'd need to know the passphrase to get in. if you turned on password auth, then you need to change these settings:

RSAAuthentication no
PubkeyAuthentication no

also, I have noticed that if you get a failure when you do nxserver --status I have still been able to log in remotely so I am not sure what that's all about. this is what I suggest. at least get password auth working with nxserver and your ssh server. wha I did was change the nxserver, nxnode so that instead of using the nx database and nx user, I changed it to use pam which is how you authenticate everything on your machine. this is what I did. i have to be honest, I never could get it to work with a custom made key so I am very confident in my password, it's very smart. BUT, i actually don't even use nxserver anymore, I have become pretty good from the cli and can do most of my server admin thru ssh so I went back to key pair auth. good luck

I have ssh doing just password now, at least the nx client doesn't show publickey when it fails now.  Still it won't connect:

```
NX> 203 NXSSH running with pid: 3496
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: xxx.xxx.xxx.xxx on port: 443
NX> 202 Authenticating user: nx
NX> 204 Authentication failed.
```

I have the port changed in node.conf and ssh.  I can log into shh on that port with no problem.  I've tried logging in as user "nx" as well as various other users.  Same problem.

How do I change nxserver & nxnode to use PAM?  I don't see any mention of that in the config files.  I just see a mention of using "nx user db" and "nx password db" in server.cfg, which is disabled.

Any other ideas?

---

### Post by dannyboy79 on 2007-05-15
> **stoneattic said:**
> I have ssh doing just password now, at least the nx client doesn't show publickey when it fails now.  Still it won't connect:

```
NX> 203 NXSSH running with pid: 3496
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: xxx.xxx.xxx.xxx on port: 443
NX> 202 Authenticating user: nx
NX> 204 Authentication failed.
```

I have the port changed in node.conf and ssh.  I can log into shh on that port with no problem.  I've tried logging in as user "nx" as well as various other users.  Same problem.

How do I change nxserver & nxnode to use PAM?  I don't see any mention of that in the config files.  I just see a mention of using "nx user db" and "nx password db" in server.cfg, which is disabled.

Any other ideas?


well that's what I was talking about. you need to make sure all settings in the node and the server have the nx user database turned off so you can log in as your own username. as I said, I had this working briefly but realized that I didn't need gui admin capabilitites and do everythign thru cli now. maybe if you're at your ropes end, try to use VNC tunneled thru ssh.

**have you tried reading this:**
[http://ubuntuforums.org/showthread.php?p=2591288](http://ubuntuforums.org/showthread.php?p=2591288)



**and then I believe he is pointing at this:**
--------------------------------------------------------------------------------

Volvoguy, I have your solution. Well, at least I hope I do. I was having the exact same problem as you. This is a version of Ubuntu that I have upgraded since Hoary. The problem had to do with the font paths. 

Check out ~/.nx/<some-unique-directory-name>/status. Mine had a line that read fatal server error, could not find font 'fixed'. The unique name is just random letters and numbers. It creates a new directory each time.

I had to modify /usr/NX/etc/node.cfg. I added this line:

AGENT_EXTRA_OPTIONS_X="-fp /usr/share/X11/fonts/misc:/usr/share/X11/fonts/cyrillic:/usr/share/X11/fonts/Type1:/usr/share/X11/fonts/CID:/usr/share/X11/fonts/100dpi:/usr/share/X11/fonts/75dpi:/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType:/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

I restarted the nxserver and then it worked. I hope this helps.

$ sudo /usr/NX/bin/nxserver --stop
$ sudo /usr/NX/bin/nxserver --start

---

### Post by mootpoint on 2007-07-09
All,

I installed the 3 pieces of software from nomachine.com on my Ubuntu Feisty laptop, and installed the windows client on a PC. When I try to connect to the laptop, I get the following in /var/log/messages:

Jul  9 16:09:04 localhost NXSERVER-3.0.0-61[6340]: User 'dennis' logged in from '172.28.175.177'. 'NXLogin::set'
Jul  9 16:09:04 localhost NXSERVER-3.0.0-61[6340]: Selected node host:localhost with port:22 'main::selectNode'
Jul  9 16:09:04 localhost NXSERVER-3.0.0-61[6340]: Current selected node: localhost is in status: running  'main::selectNode'
Jul  9 16:09:04 localhost NXSERVER-3.0.0-61[6340]: Selected session type: unix-gnome allowed in the profile of user: dennis 'NXShell::Static'
Jul  9 16:09:05 localhost NXSERVER-3.0.0-61[6340]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.0.0-76  (Error id e625037) [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 ERROR: Mon Jul  9 16:09:08 2007 running as user: 'dennis' (uid: 1000) on '' [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 ERROR: execution of last command failed [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/dennis/.nx/C-lapdog-1008-039BDFFD111DEAD24BD21660A54A602B/scripts/authority' [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 exit value: 1 [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 stdout:  [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 stderr: xauth:  /home/dennis/.Xauthority not writable, changes will be ignored [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 . [e625037] Logger::log nxnode 2813
Jul  9 16:09:08 localhost NXNODE-3.0.0-76[6365]: ERROR: NX> 596 init: stdin arguments: user=dennis,userip=172%2e28%2e175%2e177,uniqueid=039BDFFD111DEAD24BD21660A54A602B,display=1008,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=localhost,balance_host_realip=172%2e28%2e175%2e178,encryption_mode=1,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=Laptop,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=800x600x32%2brender,keyboard=pc102%2fen_US,geometry=800x600,link=lan Logger::log nxnode 2813
Jul  9 16:09:09 localhost NXNODE-3.0.0-76[6365]: getting agent pid: cannot read pid file '/home/dennis/.nx/C-lapdog-1008-039BDFFD111DEAD24BD21660A54A602B/pids/agent'. Exiting. main::get_agent_pid nxnode 8371
Jul  9 16:09:09 localhost NXNODE-3.0.0-76[6365]: directory '/home/dennis/.nx/C-lapdog-1008-039BDFFD111DEAD24BD21660A54A602B' moved into '/home/dennis/.nx/F-C-lapdog-1008-039BDFFD111DEAD24BD21660A54A602B' for investigation Logger::log nxnode 8428
Jul  9 16:09:09 localhost NXSERVER-3.0.0-61[6340]: ERROR: (exception id 18A2C753)  at NXNodeExec.pm line 1169
Jul  9 16:09:09 localhost NXSERVER-3.0.0-61[6340]: ERROR: (exception id 18A2C753) NXNodeExec::exec('startsession', 'user=dennis&userip=172%2e28%2e175%2e177&uniqueid=039BDFFD111DEAD...', 'localhost', 22) called at handlers/nxserver.pl line 3175
Jul  9 16:09:09 localhost NXSERVER-3.0.0-61[6340]: ERROR: (exception id 18A2C753) NXShell::handler_session_start('--link="lan" --backingstore="1" --cache="16M" --images="64M" --s...') called at NXShell.pm line 373
Jul  9 16:09:09 localhost NXSERVER-3.0.0-61[6340]: ERROR: (exception id 18A2C753) NXShell::handle_command('startsession', '--link="lan" --backingstore="1" --cache="16M" --images="64M" --s...') called at NXShell.pm line 145
Jul  9 16:09:09 localhost NXSERVER-3.0.0-61[6340]: ERROR: (exception id 18A2C753) NXShell::run() called at nxserver.pl line 4295
Jul  9 16:09:09 localhost NXSERVER-3.0.0-61[6340]: ERROR: (exception id 18A2C753) eval {...} called at nxserver.pl line 4254

The first error indicates nxssh is unhappy and exiting. ssh server has been running fine on the laptop for months. It doesn't seem to be authentication; here are the lines from /var/log/auth.log:

Jul  9 16:09:02 localhost sshd[6324]: Accepted publickey for nx from 172.28.175.177 port 1049 ssh2
Jul  9 16:09:02 localhost sshd[6335]: (pam_unix) session opened for user nx by (uid=0)
Jul  9 16:09:04 localhost sshd[6347]: Accepted password for dennis from 127.0.0.1 port 1117 ssh2
Jul  9 16:09:04 localhost sshd[6351]: (pam_unix) session opened for user dennis by (uid=0)
Jul  9 16:09:04 localhost sshd[6351]: (pam_unix) session closed for user dennis
Jul  9 16:09:05 localhost sshd[6360]: Accepted password for dennis from 127.0.0.1 port 1119 ssh2
Jul  9 16:09:05 localhost sshd[6364]: (pam_unix) session opened for user dennis by (uid=0)
Jul  9 16:09:09 localhost sshd[6364]: (pam_unix) session closed for user dennis
Jul  9 16:09:10 localhost sshd[6335]: (pam_unix) session closed for user nx

Any ideas out there? 

m00t

---

### Post by phisher1 on 2007-07-29
delete this post

---

### Post by BadServo on 2007-08-07
I've been able to install the NX server/client and can connect to my home workstation with no problem.  However, there is one thing that I would love to be able to do, that I've yet to manage.

Is it possible to configure the server so that when you connect remotely, you connect to the already running X session on the server?  That is, is it possible that I could log into my home PC locally, open various GUI apps, lock the workstation so those tasks could complete, and then log into the home PC remotely from the office to resume working on those tasks?

Likewise, could I log in remotely, start applications, lock/disconnect, and then resume workign with those open applications once I return home?

Any assistance is greatly appreciated.

---

### Post by davidonabus on 2007-08-23
Hey Guys.

I followed the instructions on the frontpage... but this is where I'm stuck.  When I try to access the comp from another computer this is the error I get.

I know a few other people had a similar problem but I couldn't follow the solutions.  I'm a linux newb so detailed instructions would be helpful!  Thanks guys.

david

> NX> 203 NXSSH running with pid: 14723
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 72.112.121.188 on port: 877
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.0.0-63 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: david
NX> 102 Password: *********
NX> 103 Welcome to: davidslinux user: david
NX> 105 Listsession --user="david" --status="suspended\054running" --geometry="2560x1600x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: david
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="David\047s\040Comp" --type="unix-gnome" --geometry="1650x1080+455+220" --client="macosx" --keyboard="query" --screeninfo="1650x1080x32+render" 
NX> 502 ERROR: Public key authentication failed
NX> 502 ERROR: NX server was unable to login as user: david
NX> 502 ERROR: Please check that the account is enabled to login,
NX> 502 ERROR: the user's home directory, the directory ~/.ssh
NX> 502 ERROR: and the file ~/.ssh/authorized_keys2 have correct
NX> 502 ERROR: permissions setting according to the StrictModes
NX> 502 ERROR: of your SSHD configuration.
NX> 999 Bye.
NX> 280 Ignoring EOF on the monitored channel
Killed by signal 15.

---

### Post by davidonabus on 2007-08-24
Anyone with an idea?

Thanks guys!

---

### Post by geno_rexracer on 2007-10-10
> **jkbrowne said:**
> Ok, I've fought with this off and on for a-while, but I finally found the right combination.  First of all, forget freeNX.  The NoMachine folks have released a "desktop" edition of their latest product called "NX Desktop Server" that is free for personal use (2 users/connections).  

Before proceeding, be sure to *completely* remove any previous versions of any of the FreeNX files or libraries.  Undo what you have already done, and remove the FreeNX source URLs from your /etc/apt/sources.list.


-----------------------
Step 1 - Download
-----------------------

Download "NX Desktop Server DEB for Linux" from:
[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Download "NX Node DEB for Linux" from:
[http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

Download "NX Client DEB for Linux" from:
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

-----------------------
Step 2 - Install
-----------------------
Install the DEB files in this order:

nxclient
nxnode
nxserver

I just right-clicked on them and installed them...use apt-get if you prefer.

-----------------------
Step 3 - Configure
-----------------------
Load up your /etc/ssh/sshd_config file into an editor:

sudo nano /etc/ssh/sshd_config

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart

Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status

This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration.  If not, then NX Desktop Server should be installed.

Before anyone complains, yes, I'm using the NoMachine server key just because it's easy.  If you want to generate your own key, you can.  These instructions worked for me on Dapper....YMMV.  Let me know if you have trouble.....hopefully my notes were correct.

Good luck!
A very nice post jkb, professional and well written.

I would like to add the following for those using 64 bit versions of kUbuntu:

You need to add some information from this thread on the noMachine website for these instructions to work on 64bit kUbuntu (not tested or probably needed on Ubuntu since vncserver is built-in and not buggy like krfb):

[http://www.nomachine.com/ar/view.php?ar_id=AR07D00407](http://www.nomachine.com/ar/view.php?ar_id=AR07D00407)

Specifically:  install the prerequisites as mentioned in the above link and alter each installation line in the jkb instructions to use "dpkg -i --force-architecture FILENAME" instead of right-clicking.  You need to do this for the client, node and server and all other instructions work great.

---

### Post by temak28 on 2008-01-04
Hi all, found this thread while working on a resolution to my issue. I am running Ubuntu 7.10 and connecting to server from Windows XP client. I setup everything as jk mentioned in the first post, without freenx. Used dpkg to setup client, then node then server. Everything is running fine. However, I can't for the life of me figure out what's going on with the keys. I even enabled the DB in the server.cfg file and still get Authentication login failure. Here's the error I get in the Details of NX Client and when doing ./nxserver --useradd usrname

```
root@guest-desktop:/usr/NX/home/nx/.ssh# /usr/NX/bin/nxserver --useradd usrname
NX> 900 Setting password for user: usrname.
NX> 102 Password:
NX> 102 Confirm password:
NX> 110 Password for user: usrname added to the NX password DB.
NX> 900 Adding public key for user: usrname to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: usrname.
NX> 910 WARNING: The SSH  key to be used for user authentication was
NX> 910 WARNING: added to the private authorized keys file of user
NX> 910 WARNING: but user authentication didn't succeed.
NX> 910 WARNING: Please note that, with these settings, the user won't
NX> 910 WARNING: be able to successfully run any sessions.
NX> 910 WARNING: Run the following command to get some hints on the possible
NX> 910 WARNING: reasons of the problem:
NX> 910 WARNING:
NX> 910 WARNING: nxserver --usercheck usrname
NX> 910 WARNING:
NX> 999 Bye.

```

and when running ./nxserver --usercheck usrname I get the following error:

```
X> 900 Verifying public key authentication for NX user: usrname.
NX> 900 Adding public key for user: usrname to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: usrname.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: usrname
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.

```

Strictmodes are enabled and I do have teh authorized_keys2 in the sshd config as well. I'm not sure about the permissions though.

If someone could help me with this bit, I would greatly appreciate it.

Thank you for your time

---

### Post by temak28 on 2008-01-04
Just for reference, I did double check the permissions on ~usrname/.ssh and the authorized2 file. The files are modded 0600 and the directory is 0700. So, that looks correct. Still not sure what's causing the error.

---

### Post by flade on 2008-01-29
I'm little confused with nomachine.

On debian 4 etch box nomachine installed ok. I can login and see desktop - great. (no key authentication)

Now problem is on  ubuntu feisty (7.04). I keep getting this error: 

NX> 505 ERROR: Error occurred: public key authentication failed.
NX> 505 ERROR: NX server was unable to login as user: ignacij.
NX> 505 ERROR: There is no public key on node 127.0.0.1.
NX> 280 Exiting on signal: 15

I did compare config files with each box but stiull no luck.

i tried using key files as well as user authentication but no luck.

any idea ?

---

### Post by simmo23 on 2008-02-14
I am looking for some help to solve an interesting puzzle.  I have a new install of xubuntu 7.10 working just fine on an old PC that I'm hoping to turn into a headless backup device.  I'm able to connect to the machine from a Mac OS X box on the local network using ssh or even nxssh.  I've been able to get x11vnc going and access the xubuntu machine's desktop from the Mac using 'Chicken of the VNC' without issue.  I'd prefer to use nomachine nxserver and nxclient since it seems to be a more elegant solution.  Here's where I run into an interesting problem.  I followed the instructions from jkbrowne (thank you) to configure nxserver and other posts for nxclient.  The nxclient is EVER SO CLOSE to connecting.  Here are some lines from pertinent log files:

Client side:

> 
NX> 203 NXSSH running with pid: 3979
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XXXX:X::XXX:XXXX:XXXX:XXXX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 286 Failed to set IPTOS_LOWDELAY on descriptor: 10
HELLO NXSERVER - Version 3.1.0-4 - LFE
NX> 105 Hello NXCLIENT - Version 3.1.0
NX> 598 ERROR: an error occurred when serving the request, check log file for details
NX> 999 Bye.
NX> 280 Exiting on signal: 15


Note the address there that i've X'd out is in IPv6 format and does correspond to the correct address for the client.  The tail end of the messages logfile in /var/log on the xubuntu (server) machine gives a tantalizing clue (so as not to spam on only the last 4 lines are shown)

> 
Feb 14 16:51:23 olddell NXSERVER-3.1.0-4[8819]: DEBUG: received command 'hello' 'NXCLIENT - Version 3.1.0' 'NXShell::get_command'
Feb 14 16:51:24 olddell NXSERVER-3.1.0-4[8819]: DEBUG: handling command 'hello' 'NXCLIENT - Version 3.1.0' 'NXShell::handle_command'
**Feb 14 16:51:24 olddell NXSERVER-3.1.0-4[8819]: ERROR: Get client ip failure, environment SSH_CONNECTION or SSH_CLIENT are not in the expected format (environment was 'XXXX::XXX:XXXX:XXXX:XXXX%eth0 63889 YYYY::YYY:YYYY:YYYY:YYYY%eth0 22') NXClientConnection::getRemoteIp handlers/nxserver 996**
Feb 14 16:51:24 olddell NXSERVER-3.1.0-4[8819]: DEBUG: handling command 'exit' '' 'NXShell::handle_command'



The error line seems to point to the env variables SSH_CONNECTION as the culprit - "not in expected format".  The text seems to be consistent with SSH_CONNECTION in IPv6 and both addresses do correspond to the correct addresses.  

When I check out the env variables during a ssh or nxssh session, SSH_CONNECTION appears exactly as in the log file above (IPv6) and this eventuality clearly does not prevent a successful session.  Furthermore, I can force ssh or nxssh to work with IPv4 from the command line, the SSH_CONNECTION variable ends up in IPv4 and I also succeed with a ssh or nxssh session.  The sshd_config file on the xubuntu machine has the pertinent variable set to accept either IPv4 or IPv6 (actually this is the default).

I am at a loss as to how to proceed from here and open to suggestions.  nxserver seems to force nxssh to skip reading config files (see first log above).  I can't seem to find a way to force nxclient to invoke nxssh using the IPv4 syntax.

---

### Post by goofrider on 2008-02-19
> **simmo23 said:**
> I am looking for some help to solve an interesting puzzle.  I have a new install of xubuntu 7.10 working just fine on an old PC that I'm hoping to turn into a headless backup device.  I'm able to connect to the machine from a Mac OS X box on the local network using ssh or even nxssh.  I've been able to get x11vnc going and access the xubuntu machine's desktop from the Mac using 'Chicken of the VNC' without issue.  I'd prefer to use nomachine nxserver and nxclient since it seems to be a more elegant solution.  Here's where I run into an interesting problem.  I followed the instructions from jkbrowne (thank you) to configure nxserver and other posts for nxclient.  The nxclient is EVER SO CLOSE to connecting.  Here are some lines from pertinent log files:

Client side:

```

NX> 203 NXSSH running with pid: 3979
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XXXX:X::XXX:XXXX:XXXX:XXXX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 286 Failed to set IPTOS_LOWDELAY on descriptor: 10
HELLO NXSERVER - Version 3.1.0-4 - LFE
NX> 105 Hello NXCLIENT - Version 3.1.0
NX> 598 ERROR: an error occurred when serving the request, check log file for details
NX> 999 Bye.
NX> 280 Exiting on signal: 15

```


Note the address there that i've X'd out is in IPv6 format and does correspond to the correct address for the client.  The tail end of the messages logfile in /var/log on the xubuntu (server) machine gives a tantalizing clue (so as not to spam on only the last 4 lines are shown)

```

Feb 14 16:51:23 olddell NXSERVER-3.1.0-4[8819]: DEBUG: received command 'hello' 'NXCLIENT - Version 3.1.0' 'NXShell::get_command'
Feb 14 16:51:24 olddell NXSERVER-3.1.0-4[8819]: DEBUG: handling command 'hello' 'NXCLIENT - Version 3.1.0' 'NXShell::handle_command'
Feb 14 16:51:24 olddell NXSERVER-3.1.0-4[8819]: ERROR: Get client ip failure, environment SSH_CONNECTION or SSH_CLIENT are not in the expected format (environment was 'XXXX::XXX:XXXX:XXXX:XXXX%eth0 63889 YYYY::YYY:YYYY:YYYY:YYYY%eth0 22') NXClientConnection::getRemoteIp handlers/nxserver 996
Feb 14 16:51:24 olddell NXSERVER-3.1.0-4[8819]: DEBUG: handling command 'exit' '' 'NXShell::handle_command'

```

The error line seems to point to the env variables SSH_CONNECTION as the culprit - "not in expected format".  The text seems to be consistent with SSH_CONNECTION in IPv6 and both addresses do correspond to the correct addresses.  

When I check out the env variables during a ssh or nxssh session, SSH_CONNECTION appears exactly as in the log file above (IPv6) and this eventuality clearly does not prevent a successful session.  Furthermore, I can force ssh or nxssh to work with IPv4 from the command line, the SSH_CONNECTION variable ends up in IPv4 and I also succeed with a ssh or nxssh session.  The sshd_config file on the xubuntu machine has the pertinent variable set to accept either IPv4 or IPv6 (actually this is the default).

I am at a loss as to how to proceed from here and open to suggestions.  nxserver seems to force nxssh to skip reading config files (see first log above).  I can't seem to find a way to force nxclient to invoke nxssh using the IPv4 syntax.

I'm experiencing that same problem. My NoMachine NX nxserver daemon worked fine until I upgraded it today to the latest version and the daemon starts complaining about the IPv6-formatted SSH_CONNECTION envar.

The funny thing is that I think I've seen the problem before but I forgot how I fix it last time. How I fixed it this time? Uninstall NoMachine NX and install FreeNX.  :P    Apparently Gutsy packages are finally available.

Another funny thing: I was running NoMachine's version of NX in the first place was mostly because I got tired of FreeNX breaking each time I upgrade to a new release of Ubuntu.

Wish FreeNX can get in Universe soon and put us all out of our misery.

---

### Post by daflame on 2008-02-22
> **goofrider said:**
> I'm experiencing that same problem. My NoMachine NX nxserver daemon worked fine until I upgraded it today to the latest version and the daemon starts complaining about the IPv6-formatted SSH_CONNECTION envar.

The funny thing is that I think I've seen the problem before but I forgot how I fix it last time. How I fixed it this time? Uninstall NoMachine NX and install FreeNX.  :P    Apparently Gutsy packages are finally available.

Another funny thing: I was running NoMachine's version of NX in the first place was mostly because I got tired of FreeNX breaking each time I upgrade to a new release of Ubuntu.

Wish FreeNX can get in Universe soon and put us all out of our misery.

You could also follow the walk through here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)
to move to FreeNX instead.  Works great for me.  It also doesn't have connection limitations like NX Free Edition does.

---

### Post by 77_Chris on 2008-02-25
Hi!
Has someone solved this problem in the meantime ?

```

NX> 502 ERROR: Public key authentication failed
NX> 502 ERROR: NX server was unable to login as user: david
NX> 502 ERROR: Please check that the account is enabled to login,
NX> 502 ERROR: the user's home directory, the directory ~/.ssh
NX> 502 ERROR: and the file ~/.ssh/authorized_keys2 have correct
NX> 502 ERROR: permissions setting according to the StrictModes
NX> 502 ERROR: of your SSHD configuration.

```

I've been using nxserver for quite a while and until yesterday everything went fine.
Then I installed an new driver for my ATI 2600 graphics card and I could no longer login from winXP via nxclient.

I've checked sshd_config, node.cfg, well configured.
I can login via ssh-client without any problems, nxserver --status says everything's fine.

I've also removed all nx packages and have done a complete reinstall. But without success.

I have no idea what's going on, could someone help me?

Greetings, Chris

I forgot to mention: Ubuntu is 7.10. Nxserver, nxnode and nxclient newest available from [www.nomachine.com](www.nomachine.com)

/**
 * Solved
 */

OK, nxserver is up again.

What was the problem?
I had to use port 443 for some reason and so I changed the values of SSHDPort to "443" in node.cfg and server.cfg but I did not change SSHDAuthPort to "443" in server.cfg.
After changing that value too, everything was running fine again.

It is a bit curious, because as originally stated, my configuration was already running without setting the SSHDAuthPort value until it suddenly broke.

Cheers, Chris

---

### Post by matpil on 2008-03-12
Hi all!

I've some problems qith nxserver and xubuntu.

I use ubuntu on my desktop pc and all works fine. On my laptop I installed xubuntu and here have some problem.

First of all, I've had some difficulties to connect to X server (I had startxfce4 command to my nx client).

Now I can connect (in my office I use windows to connect to my home laptop) but seems that all it's "freeze". On top of that, when I connect to my laptop, on my office pc it's open 3 windows: 1) my laptop desktop; 2) application bar (on top) and 3) "application running" bar (on bottom).

It's correct?!?!?

Other problem...

if I check the status of my nxserver I've a strange result...
```

root@linux-NB:/# /usr/NX/bin/nxserver --stop
NX> 500 Service was already stopped.
NX> 999 Bye.
root@linux-NB:/# /usr/NX/bin/nxserver --start
NX> 122 Service started.
NX> 999 Bye.
root@linux-NB:/# /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
root@linux-NB:/#

```

Can anyone help me?

Regard,
matpil

---

### Post by goofrider on 2008-03-16
> **daflame said:**
> You could also follow the walk through here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)
to move to FreeNX instead.  Works great for me.  It also doesn't have connection limitations like NX Free Edition does.

I am using FreeNX now, but FreeNX has it's own problems.

1. FreeNX has trouble supporting my mac client with 2 desktops (MacBook LCD + ext LCD).

2. FreeNX has screen redraw issues

3. FreeNX breaks everytime with each Ubuntu release and require reinstallation

---

### Post by simmo23 on 2008-03-16
I tried following the walk-through (daflame thank you for suggesting it and for your hard work in posting it) but couldn't get FreeNX functioning.  I got an obscure error message in the log file (something along the lines of connection rejected).  I have officially given up with either nomachine or FreeNX.  I do have x11vnc working with chicken of the vnc as a client but I don't think it allows me to really run the machine headless.

---

### Post by victorgreen on 2008-07-18
matpil, Im having the exact same problem you are. Im running 64bit hardy. When I try to connect in the connection always times out and the server in status says its running but then isnt. If I tell it to start it says already started and if I tell it to stop it says already stopped. In any case no NX process is running on my computer

---

