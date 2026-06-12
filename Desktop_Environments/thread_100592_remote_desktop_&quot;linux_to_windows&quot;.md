---
title: "remote desktop &quot;linux to windows&quot;"
date: 2005-12-07
forum: Desktop Environments
---

### Post by raven on 2005-12-07
I know there is some threads about this,
but I could not find a linux to windows combination with a good how to.
Most of them talked about windows to linux, and I could not find freeNX server for windows.
I have 1 linux (breezy) box and I need to have  GUI connection to 2 winxp's
1 of the XP's it is on LAN, and the other XP on the internet
can anyone be kind and tell me what 
linux (breezy) client, (main points security and speed) and
2 XP's servers, 1 on LAN and 1 on internet (main points security and speed)
internet connection on the winxp is a bit slow
any suggestion on the best combination ?

---

### Post by pete on 2005-12-07
Your best bet for Linux->XP is to use the Terminal Server Client that comes with Ubuntu.  It's under Applications-Internet.  Change the protocol to RDP, and make sure that the XP boxes are set up to allow incoming RDP sessions.  (Right-click My Computer, go to Properties, and then the Remote tab; check the box next to "Allow users to connect remotely to my computer".)

If the XP box that is on the Internet is behind a router/firewall, you'll need to set the firewall to open port 3389, and probably forward it to the XP box.

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=raven]I know there is some threads about this,
but I could not find a linux to windows combination with a good how to.
Most of them talked about windows to linux, and I could not find freeNX server for windows.
I have 1 linux (breezy) box and I need to have  GUI connection to 2 winxp's
1 of the XP's it is on LAN, and the other XP on the internet
can anyone be kind and tell me what 
linux (breezy) client, (main points security and speed) and
2 XP's servers, 1 on LAN and 1 on internet (main points security and speed)
internet connection on the winxp is a bit slow
any suggestion on the best combination ?[/QUOTE]

XP Pro or XP Home?  I think you can remote desktop into XP Pro, but I don't think XP Home has a terminal server.  I use rdesktop to connect to my Win2K machine at work.

Otherwise, VNC is probably your best option.  If you want it secure, the best you can do is set up an ssh server on the XP box and ssh into it from Ubuntu.  You forward the VNC port and then connect your VNC viewer to localhost.

---

### Post by Joe_CoT on 2005-12-07
two ways

1) You can use rdesktop for linux. this is a program that uses the remote desktop connection built into windows xp. you'd just need to enable remote desktop on the two windows boxes
on windows boxes:
control panel: system, remote tab, enable remote desktop connection
on the ubuntu box:
```
sudo apt-get install grdesktop
```
then just run grdesktop (i'm not sure if it adds itself to the applications menu or not. if it doesn't either add it or run grdesktop from the console) and connect to the boxes.

2) install vnc on the windows boxes and the ubuntu box

on the windows box:
download [tightvnc](http://www.tightvnc.com/download.html) and install and configure it

on the ubuntu box:
```
sudo apt-get install xtightvncviewer tightvncserver
```
then run xtightvncviewer from the console

---

### Post by raven on 2005-12-07
both are XPpro
what about if I want to drag a file from the winxp desktop to my linux box
is it possible ? if yes how ?


by the way it's working through terminal server client

and guys I appreciate the answers and the help
it was faster than a phone call to tech support

Thanx again

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=raven]both are XPpro
what about if I want to drag a file from the winxp desktop to my linux box
is it possible ? if yes how ?


by the way it's working through terminal server client

and guys I appreciate the answers and the help
it was faster than a phone call to tech support

Thanx again[/QUOTE]
You need to install and configure samba for file sharing on Ubuntu.  Then you share a folder.  From XP, you will be able to open a network share just like you would from another XP computer.

There is no drag and drop directly from RDP or VNC from one desktop to another, no matter what OS you are using as far as I know.  Other ways to transfer files would be to set up an ssh server or an FTP server on one of the machines.

---

### Post by atoponce on 2005-12-08
[quote=cwaldbieser]XP Pro or XP Home?  I think you can remote desktop into XP Pro, but I don't think XP Home has a terminal server.  I use rdesktop to connect to my Win2K machine at work.[/quote] Neither one of them come shipped with terminal server.  Terminal server requires licensing from Microsoft which in turn requires fees, and they aint cheap.  Remote desktop is available by default for XP Pro, and can be downloaded for free to XP Home.  Terminal server is only available for Windows 2000 and 2003.

---

### Post by handy on 2005-12-08
Hi,
I set up an xp lan, some years ago now for a car dealer, we had to use xp pro' because it had the relevant services on which to run terminal server.  It was some years ago now so I'm sorry I can't remember any more details.

Probably not much help, but it does all add up :-)

Cheers,

handy

---

### Post by Joeak on 2005-12-08
You can use openssh from openssh.org and the free version of Realvnc 4.1 from realvnc.com on your XP machines to provide SSH and VNC services on XP.  Set up properly only port 22 needs to be accessible over the Internet, and you can tunnel either RDP or VNC sessions through it so it's pretty secure.  SSH also can be used for SFTP secure file transfer to and from the XP machines, just like it is used by *nix admins.

---

### Post by Joeak on 2005-12-08
[QUOTE=cwaldbieser]...You forward the VNC port and then connect your VNC viewer to localhost.[/QUOTE]

FYI, with the Linux version of vncviewer, you can launch vnc and tell it to set up the tunnel with one line with the "-via" parameter.

vncviewer -via <user>@<remotemachine> -truecolour -geometry 1024x768 localhost:0

As far as I can tell the -via only works in Linux.  Windows ignores the parameter, and if you use the command above literally it generates a loop opening vncviewer on localhost:0.

---

### Post by pete on 2005-12-08
[QUOTE=atoponce]Neither one of them come shipped with terminal server.  Terminal server requires licensing from Microsoft which in turn requires fees, and they aint cheap.  Remote desktop is available by default for XP Pro, and can be downloaded for free to XP Home.  Terminal server is only available for Windows 2000 and 2003.[/QUOTE]

This may be more of sidebar than anyone needs, but just to be clear, although the remote desktop functionality within XP is based on Terminal Services, we're not talking about running a terminal server here.  The ability to accept an incoming RDP session is built into XP Pro, as is the Remote Desktop client that would allow you to initiate an RDP session to another box.  

However, while the Remote Desktop client can be installed on an XP Home box, there is no way that I know of for an XP Home box to receive an incoming RDP session.

As for 2K and 2k3, you do *not *need additional licenses if all you want to do is have a single Remote Desktop session.  Additional licensing is required if you want to run a Terminal Server that supports multiple concurrent terminal sessions.

---

### Post by atoponce on 2005-12-08
[quote=pete]This may be more of sidebar than anyone needs, but just to be clear, although the remote desktop functionality within XP is based on Terminal Services, we're not talking about running a terminal server here.  The ability to accept an incoming RDP session is built into XP Pro, as is the Remote Desktop client that would allow you to initiate an RDP session to another box.  

However, while the Remote Desktop client can be installed on an XP Home box, there is no way that I know of for an XP Home box to receive an incoming RDP session.

As for 2K and 2k3, you do *not *need additional licenses if all you want to do is have a single Remote Desktop session.  Additional licensing is required if you want to run a Terminal Server that supports multiple concurrent terminal sessions.[/quote] Correct.  And you can, AFAIK, setup a Win XP Home box to allow incoming RDP connections.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=Joeak]FYI, with the Linux version of vncviewer, you can launch vnc and tell it to set up the tunnel with one line with the "-via" parameter.

vncviewer -via <user>@<remotemachine> -truecolour -geometry 1024x768 localhost:0

As far as I can tell the -via only works in Linux.  Windows ignores the parameter, and if you use the command above literally it generates a loop opening vncviewer on localhost:0.[/QUOTE]
That's pretty cool.  Does it require the server side to be running an SSH server?

---

### Post by Joeak on 2005-12-11
[QUOTE=cwaldbieser]That's pretty cool.  Does it require the server side to be running an SSH server?[/QUOTE]

vncviewer -via <user>@<remotemachine> -truecolour -geometry 1024x768 localhost:0

The <remotemachine> has to be running SSH.  You can change the localhost parameter to point to a different machine as long as VNC is active and open from the machine with SSH to the VNC machine (i.e. on a very private home network maybe).  At my job we run this on hundreds of machines statewide, and each machine is its own openssh server to encrypt the communication all the way to the destination.

---

### Post by [HUN]Levente on 2006-04-13
[QUOTE=cwaldbieser]You need to install and configure samba for file sharing on Ubuntu.  Then you share a folder.  From XP, you will be able to open a network share just like you would from another XP computer.

There is no drag and drop directly from RDP or VNC from one desktop to another, no matter what OS you are using as far as I know.  Other ways to transfer files would be to set up an ssh server or an FTP server on one of the machines.[/QUOTE]
I want to do the same.
I connect to a Windows server using Terminal Server Client. I have Samba configured, but I can't map my linux share to Windows. How should I do it?
What to write in the Map network drive box?
Maybe I configured Samba wrong?

---

