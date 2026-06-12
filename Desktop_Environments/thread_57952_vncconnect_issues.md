---
title: "vncconnect issues"
date: 2005-08-18
forum: Desktop Environments
---

### Post by mbeach on 2005-08-18
hi,
using vncserver 3.3.7-7, there is a program called vncconnect which as I understand it is similar to the 'add new client' option in the windows vncserver.

In the man pages it says that feedback from the vncconnect program will be in the log file for Xvnc (because Xvnc actually makes the connection to the host).

When I run (on the Ubuntu box)
vncconnect remoteipaddr

seemingly nothing happens.  I can connect to the Ubuntu box using a vncviewer from my machine (Windows box).  The 'listening viewer' is running on the Windows box on port 5500 and works when 'add new client' is chosen from another Windows machine.

I had toyed with vnc4server but I got similar results, so I reverted everything back to my original setup (vnc-common 3.3.7-7, vncserver 3.3.7-7, and vino 2.10.0-0ubuntu1 [everything checked as allowed except for the 'ask you for confirmation']).

My questions:
1 - where is the Xvnc log?
2 - is there a configuration setting somewhere that I'm missing to allow 'reverse' connections that vncconnect attempts

I'm trying to setup a machine for someone who needs access to a web browser and that's it.  Since I know they won't be able to help themselves, I thought a Ubuntu desktop might be the way to go, and give them a button in the panel which would run the 
vncconnect mymachine 
which would allow me to apply patches etc remotely.

I don't believe port issues are at play here, but perhaps the Ubuntu machine cannot get out on 5500?  No software firewall installed, and the router has no blocking from lan to lan.  Both machines are connected to the same router now, but will eventually be countries apart.

I am not looking to remote the login screen (gdm).

Any pointers?
mbeach.

---

### Post by Olav on 2005-08-18
[QUOTE=mbeach]When I run (on the Ubuntu box)
vncconnect remoteipaddr

seemingly nothing happens.[/QUOTE]
Sorry, can't help you. Just bumping this back to the top of the forum because I want to know the solution, too. Having the same problem.

---

### Post by skunkydog on 2006-04-22
I'm running damn small linux but the forums here are better.  So you might not have the same issue.  Anyway...

Check your DISPLAY environment variable.  Mine was set to **:0.0** for some reason, but when I changed it to **:1**, it connected.  If your vnc server is running on display 2, set it to 2, etc.

My log files are in ~/.vnc/hostname:display.log (in my case /home/dsl/.vnc/box:1.log).  But if  the environment variable is set to the wrong display, nothing should show up in the log file since vncconnect couldn't actually talk to the vnc server.

To check the variable, type **echo $DISPLAY** in a terminal window.
To set the variable, type **export DISPLAY=:1** - or whatever display vncserver is running on.
Then do **vncconnect host**.  You'll have to do it all in the same terminal window because the variable is only set to 1 in that terminal.

hth

---

### Post by bilbothebaggins on 2007-09-01
Hello.

Check out this thread: [http://ubuntuforums.org/showthread.php?t=296347](http://ubuntuforums.org/showthread.php?t=296347)
Especially this posting: [http://ubuntuforums.org/showpost.php?p=1754988&postcount=16](http://ubuntuforums.org/showpost.php?p=1754988&postcount=16)

> **dbott67 said:**
> Hi jmvidalvia,

I've got it...  I had some computer troubles over the weekend & I had to re-install my desktop --- I decided to give edgey a try.  Anyhow, I've figured out what the problem is:

On the "remote" computer (the one that you want to control), you need to install the x11vnc package:
```
sudo apt-get install x11vnc
```
Once installed, the remote user needs to issue the following command:
```
x11vnc -connect your.computer.ip.address:5500
```

Before they can "send their desktop", you need to set vncviewer to listen-mode:
```
vncviewer -listen
```

Hope this works for you... I've just tested it on 2 laptops to connect to my home PC & it works!  Attached is a screenshot of my desktop showing the 2 remote laptops (VNC:Tecra & VNC:Dapper).

-Dave

This worked for me also. It seems since Ubuntu alread has a vnc server running by default the vncconnect method does not really work as intended.

```
x11vnc **-connect** your.computer.ip.address
```

br,
Martin

---

