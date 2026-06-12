---
title: "FreeNX terminates session immediately after login (Jaunty 9.04)"
date: 2009-05-15
forum: General Help
---

### Post by dannymac64 on 2009-05-15
I just installed FreeNX on Jaunty 9.04.  After connecting from the client via Windows XP or Hardy 8.04, the session authenticates and the black window with the big "!M" appears for a second or two.  Immediately afterward, the session is terminated and the window closes without any errors written to the logs.

Does anyone have any suggestions on how to fix this?  Read below for more detail.


The server is configured as follows:
Ubuntu 9.04 64bit (Gnome)
NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)

This happens with the latest NoMachine client (3.3.0-6) on both Ubuntu 8.04 (Gnome) and Windows XP.

/var/log/nxserver.log is empty

~/.nx/<sessionid>/errors is empty

~/.nx/<sessionid>/session:

NXPROXY - Version 3.3.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '8844'.
Session: Starting session at 'Thu May 14 23:30:44 2009'.
Info: Connection with remote proxy completed.
Info: Using WAN link parameters 768/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method 'adaptive-9' with session 'gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 1/1.
Info: Using cache file '/home/danny/.nx/cache-gnome/S-138E61CA6D87A2D788916356149CC24B'.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Thu May 14 23:30:44 2009'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Thu May 14 23:30:46 2009'.
Session: Session terminated at 'Thu May 14 23:30:46 2009'.

---

### Post by dannymac64 on 2009-06-04
I have confirmed this same thing happens when the server runs Ubuntu versions 8.10 64 bit, and 8.04.2 (64 bit and 32 bit).  

Other useful details:
 - I can ssh into the server from the client laptop
 - On the client laptop, FreeNX works just fine connecting to my work machine via ssh tunnel

It appears something else may be the culprit.
Anyone have ideas?

---

### Post by trungly on 2009-06-04
I have the same problem.  Running the freenx server on Jaunty 9.04 32-bit, and trying to connect from No Machine client on Windows 7 64-bit and Jaunty 9.04 64-bit.

Behavior is the same as dannymac described.

Danny, did you file a bug report on launchpad.net?


[Update]
Actually, for me, it's failing when the server is a 32-bit Jaunty (which was distro upgraded about two times).  But on a fairly new 64-bit Jaunty install, the freenx server is working.

---

### Post by jeditec on 2009-06-07
I have the same issue, i've tried a lot of suggestions, right now i'm able to login but just as root, i enabled the allow root login in ssh, and it works ok, but i know that's not safe, it might be a permissions problems or something like that.

ATTENTION!!!: After creating a new user from gnome, the connection works ok even if its not a root user, it keeps failing with old users.

---

### Post by shuggyboi on 2009-06-11
I can confirm this. I'm running the server on Ubuntu 9.04 Jaunty, and with old profiles it terminates just after log in. 
I created a new user through gnome and managed to successfully log in using it. 

Whats the difference between new and old profiles? I would really like to use my old profile if anyone can work this out it'd be great!

Solution! : 

Delete the .Xauthority-c and .Xauthority-l files in your home directory. 
This seemed to fix my problem, though the files are generated on boot so i need to find a way to stop that!

---

### Post by IsmailBhai on 2009-07-01
exact same problem here.

---

### Post by jeditec on 2009-07-01
My problem was solved, i dont know how or why, i did the following.
 
I followed *shuggyboi* recommendations, after that i uninstalled freenx with purge option, then i removed ssh client and server also with purge option, rebooted(in windows works hahaha), reinstalled ssh client and server and finally installed freenx using the guide at the forum, cant remember the link sorry, i didnt modified anything, just configured freenx with dpkg-reconfigure freenx-server, and choosed the normal public keys, after that it worked.
 
I then changed to my own keys and it kept working.
 
But to be sincere i dont know what fixed the problem.
 
Hope it helps a little.

---

### Post by ronan.mt.fleming on 2009-07-03
I had exactly the same p_roblem as [dannymac64]("http://ubuntuforums.org/member.php?u=580574")_
Now its SOLVED

Solution: make sure that when you configure the nxclient that it is trying to use the same desktop environment as the machine with your nxserver (freenx). The default of nxclient is KDE, but the default of ubuntu is GNOME, so click the configure button on the nxclient startup dialogue and select Desktop>GNOME if you are using GNOME on your server.

---

### Post by tidewatcher on 2009-08-13
Just want to confirm the solution and add that this seems to be a feature of the protocol, or of a common library. The clients terminate the connection without a word said about the reason; doesn't even matter which client: nomachine or qtnx -- same behavior in both cases.

The visual separation of the "Server" and "Desktop" configurations is confusing: it made me think that "Desktop" applied to the client machine, and I kept selecting "gnome" instead of "kde", which is the only wm I have on the server machine, while "gnome" is what I'm running on the client.

---

### Post by bgeneto on 2009-08-23
I can't confirm the 'solution' posted here, by selecting the correct desktop environment (KDE, Gnome or whatever) the problem still persists (running 9.04 64-bit here). The tip from Ubuntu wiki page for deleting and changing .Xauthority file permission also didn't work ([https://help.ubuntu.com/community/FreeNX]("http://help.ubuntu.com/community/FreeNX")). Of course removing all related components completely (as previous mentioned) works temporally (until the first connection and before the next server boot, I suppose). No real solution by now :-(

---

### Post by mnrbig on 2009-08-30
Hi

A solution is found on this page


[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Quote

# Problem: At the client, the !M logo window appears, but after a few seconds that window just closes, even without showing any error message.
#

Solution: In the server, access your home directory and run this command, sudo rm .Xauthority* followed by touch .Xauthority and finally chmod 600 .Xauthority . This issue is due custom VNC configuration

---

### Post by jalyst on 2009-09-05
> **bgeneto said:**
> I can't confirm the 'solution' posted here, by selecting the correct desktop environment (KDE, Gnome or whatever) the problem still persists (running 9.04 64-bit here). The tip from Ubuntu wiki page for deleting and changing .Xauthority file permission also didn't work ([https://help.ubuntu.com/community/FreeNX]("http://help.ubuntu.com/community/FreeNX")).

didn't work for me either, this did the trick for me
[http://www.sharpee.com/wordpress/?p=108](http://www.sharpee.com/wordpress/?p=108)

See the updated wiki, feel free to edit if you think it's off a bit..

---

### Post by dannymac64 on 2009-09-13
So I basically gave up and decided to use nomachine's NX server instead: [http://www.nomachine.com](http://www.nomachine.com).  The only downside is that it has a maximum two simultaneous client connection restriction, which didn't affect me.  Just make sure you completely remove all FreeNX related components before installing the server, client, and node from nomachine's website.  No more issues.

---

### Post by jalyst on 2009-09-14
i'm not having any issues, but if two's good enough for you then why bother reverting i guess!

---

### Post by drpsg on 2009-09-18
I have the same issues just after using it a week. The symptoms occured after a logout. So far non of the mentioned solutions works. I use xubuntu jaunty amd 64. I tried the following tests:
- add a new user at the server, client can connect with nx for the new user
- tried the nx connection:
ssh -i /usr/NX/share/keys/server.id_dsa.key -l nx nxserver 
  this also works
- tried to connect only the console, this works also...

There must be something wrong with X for that user...

---

### Post by drpsg on 2009-09-18
I fixed it for Xubuntu. It appears that removing the .Xauthority doesn't work for the XFCE desktop. Removing the .ICEauthority files does works for Xubuntu.

---

### Post by jalyst on 2009-09-18
well done

---

