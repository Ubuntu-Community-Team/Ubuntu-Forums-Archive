---
title: "Need help with Remote Desktop"
date: 2005-10-01
forum: Desktop Environments
---

### Post by ahood on 2005-10-01
Hi Anybody,
I would like to use the Remote Desktop tool that comes with Ubuntu; however, I am unable to get it to work.
I have two machines running Ubuntu (Hoary) on the same LAN. 
I have configured both to allow remote desktop access using the password option and not to prompt the user to ask for confirmation. 
I then try to make the connection using a terminal and the command
> vncviewer IPADDRESS:0
The output is....
> VNC viewer version 3.3.7 - built Oct 28 2004 23:56:22
Copyright (C) 2002-2003 RealVNC ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge
see [http://www.realvnc.com](http://www.realvnc.com) for information on VNC
Nothing else appears. What do I do next?
Please help!
Al Hood

---

### Post by mrcbrown on 2005-10-01
Do you have firewalls setup on either end? Secondly is there a vncserver running as well?

---

### Post by professor_chaos on 2005-10-01
If you don't care about remotely viewing the current gui, you can remotely login (graphically) via XDMCP. 
Just go "System->Administration->LoginSetup->XDMCP" and enable.

Then just use that setting from terminal client. Works for me, and other users can be logged in to that remote station and they aren't impeded by my presence.

---

### Post by ahood on 2005-10-02
[QUOTE=mrcbrown]Do you have firewalls setup on either end? Secondly is there a vncserver running as well?[/QUOTE]
Thank you for responding.
There is the linux firewall running on both machines. I have turned firestarter off, but I am not sure if this actually turns off the firewall completely. There is also a firewall running on the LAN gateway. I didn't think I needed to forward any ports because both machines are simply communicating across the LAN, rather than out to the internet. Not sure though.
I hope this has answer the question. If there is a suggestion on how to modify the software firewall (firestarter) or hardware firewall (LAN gateway), I am all for trying it.
Thanks again!
Al

---

### Post by ahood on 2005-10-02
[QUOTE=professor_chaos]If you don't care about remotely viewing the current gui, you can remotely login (graphically) via XDMCP. 
Just go "System->Administration->LoginSetup->XDMCP" and enable.
Then just use that setting from terminal client. Works for me, and other users can be logged in to that remote station and they aren't impeded by my presence.[/QUOTE]
Thank you for replying,
This sounds promising. What terminal client is suggested and how do I configure it?  This is very new to me and I need a bit of step-by-step instruction.
Thanks again!
Al

---

### Post by mrcbrown on 2005-10-02
If your going that route just the terminal client thats in Ubuntu - it has options for XDMCP, but if your going from Windows you can choose from several remote clients and or my route went cygwin running X :)

---

### Post by ahood on 2005-10-02
[QUOTE=mrcbrown]If your going that route just the terminal client thats in Ubuntu - it has options for XDMCP, but if your going from Windows you can choose from several remote clients and or my route went cygwin running X :)[/QUOTE]
Thanks again,
Is the terminal client in Ubuntu mentioned above vncviewer?
If it is, I sure wish I could get it to work. :-{
I type in the vncviewer command (i.e., vncviewer 192.168.0.xx:0 and it seems to start, but no additional window appears, just a blinking cursor. Do I type in something additional to get a window displaying the remote desktop?
I found this forum topic [http://ubuntuforums.org/showthread.php?t=42941&highlight=xdmcp+howto](http://ubuntuforums.org/showthread.php?t=42941&highlight=xdmcp+howto) but I was unsuccessful on getting the client to work. Unfortunately, this topic didn't explain in detail how to get the viewer client app working.
I am going strictly between two Ubuntu machines. The forums has a number of posts about how to connect a Windows machine remotely to an Ubuntu machine, but I haven't found an Ubuntu-to-Ubuntu post yet.
I have searched the forums quite a bit and I get bits and pieces on how to get these packages to work. Unfortunately, I don't have a clear picture of how to get the server going and the client going on two machines and communicate to each other.
Arrrrggghhh..... (hehe)
Again, any help would be greatly appreciated.
Al

---

### Post by professor_chaos on 2005-10-02
try "Terminal Server Client"
It should be installed as part of your base installation.

Just go to "Applications->Internet->Termial Server Client"
From there, it should be pretty straight forward and the GUI is quite user friendly.

I use this method, use XDMCP for remote graphical logins to other Unix/Linux desktops and RDPv5 for logins to XP desktops. VNC is useful if you want to take over the desktop (to see exactly what the person sitting in front of that desktop is seeing). Depending on your goal, you can also remotely login and also view applications graphically by simply logging on via ssh with tunneling. This is accomplished by "ssh -X username@192.168.0.1". If your username is the same on both machines then you can omit the username@. Of course, use your own IP address, or if the host is configured in /etc/hosts, then just use the hostname.  For ssh to work, you need to install ssh-server.

Ohh, and I think if you have XDMCP enabled on the remote machine, you can also login to that desktop from the login screen, by pressing F10 when you are at the login prompt.

Let us know if you still need help.

---

