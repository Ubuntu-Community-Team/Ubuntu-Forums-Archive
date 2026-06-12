---
title: "Remote access to 12.04 w/gui, w/o active local session?"
date: 2012-08-26
forum: Desktop Environments
---

### Post by mendo on 2012-08-26
I have researched this for a few days now and am about to throw in the towel.  Maybe you can help.  Thank you in advance.

I have installed Ubuntu Desktop 12.04 (32 bit) and Samba and have a simple file server running that I would like to be able to control remotely from a Windows machine.  But I want to be able to control it by a graphical interface - not by terminal.  I can access it by remote desktop as well as vnc client, but the remote desktop doesn't work correctly (no desktop icons and compiz crashes) and if I use a VNC client, there has to be someone logged into the server.  This means that if I reboot the Ubuntu system, I can't log into it remotely until I log into it locally, which means that I can't run it headless, which is really my goal.

I am not very good with Ubuntu or Linux, but have learned enough to get to this point.  Can you help me get over this hurdle?

I'm sure I've left out pertinent details - let me know what matters and I'll fill you in.  Any ideas?  Thanks!

---

### Post by steeldriver on 2012-08-26
You have a couple of different problems here I think

First is that compiz pretty much breaks VNC at the moment - I've seen various recommendations like invoking with -noxdamage etc but none of them seemed to work for me. The best solution right now seems to be to customize your config to use a 2d / gnome classic session, which uses metacity rather than compiz - something like the custom ~/.vnc/xstartup file here should work:

[https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)


Second is the remote login. I've tried that a couple of different ways:

1. use the lightdm login-session-start upstart event as described here:

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

[B]If you go this route I'd recommend adding the -local flag as described in the blog comments and then tunneling the VNC traffic over SSH
[/B]
2. use a VNC server that's specifically intended to run separate sessions on remote displays rather than provide a 'desktop sharing' environment, e.g. tightvncserver

I have not done so but you could configure this to run on boot and always start a session for a particular user on a known display however I'd again recommend SSH tunneling, and if you're firing up putty to make the tunnel then it's really no extra work to invoke the VNC server from putty at the same time. In practice you can pretty much leave the session running after that (I have a VNC session on a server at work that's been up for weeks - I just pop in and out of it from home via putty / TightVNC viewer).

Having tried both, the 2nd of these would be my preferred route now. Basically if you use SSH tunneling they are the same amount of effort from the Windows side.

I'm sure other folks will have suggestions as well - FreeNX is popular but I'm not sure the status of Windows clients for that, someone else will chime in on that I'm sure

---

### Post by OM55 on 2012-08-27
VNC is one option, but definitely not the only one and not the fastest one. Here are two more good options:

1. If you want something like LogMeIn (with no massing with port forwarding on the router and static IPs) than you can use **Team viewer** (**[http://www.teamviewer.com](http://www.teamviewer.com)**). The free version would be good for most basic applications. They have client and servers to all major operating systems.


[I] Keep in mind that with VNC or TeamViewer you will be working on the active session currently on the Ubuntu machine. So you will not work in the background and anyone seating in front of the Ubuntu machine will see what you are doing.
[/I] 

2. If you want an RDP style connection (like Remote Desktop Connection in Windows) use NX Server and Client. There is a native server version for Ubuntu 12.04 and clients both for Ubuntu 12.04 and Windows. It would considerably faster than VNC or TeamViewer AND will work in the background - meaning you can connect remotely and work on the Ubuntu machine in your own graphic environment, without interfering with the local Ubuntu user's screen.

To install NX Server on the Ubuntu 12.04 machine (for older versions a different process is required) type in terminal:
```

    sudo add-apt-repository ppa:freenx-team/ppa 
    sudo apt-get update
    sudo apt-get install freenx-server

```To install the NX client for Ubuntu, Windows or Mac, download the latest client from:
**[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)**

The usernames and passwords for access will be the same one on the Ubuntu machine.
If you are behind firewall or NAT router, you will need to forward port 22 to the Ubuntu machine.

Hope that helps!

---

### Post by mendo on 2012-08-30
Thanks for the help, both of you.  I finally got some time to play with this and took a whack at the freenx option first (no offense, steeldriver).  The terminal commands seemed to run ok - no errors or anything.  I downloaded the nx client for my windows machine, but haven't been able to connect to the ubuntu machine.  I keep getting "Authentication failed for user Mendo" and the Detail button is gray, so I can't click on it - I guess that means that I shouldn't need any other details.

I didn't change anything on any of the NX Client configuration tabs except General.  I set the Host IP address, left Port at 22, have it set for VNC and then clicked on Settings.  In Settings, I set the Host IP address, set port to 22 and entered my user password for the Ubuntu machine.

Once all of that was set, I click Login from the main NX Client Window with the same username & password I would use to login locally from the Ubuntu machine.  First it says "setting up the environment", then "connected to 192.168.1.118', then "waiting for authentication", the "authentication failed for user Mendo".

Ubuntu IP (Host): 192.168.1.118
NX Client: Port: 22

Any ideas?  I feel like I'm really close and just screwing something up with the password or port or something.

FWIW - I made an image of the clean install and have been restoring it before I try a new method of remotely connecting without being logged in locally.  I update it and then try something new.  There shouldn't be anything weird about my install - it's almost exactly off-the-shelf.

Thanks again for any help!!

---

### Post by OM55 on 2012-08-31
This may happen if you mistype the username (or password). A typical mistake when connecting from Windows is to capitalize the first latter of the username while in Linux the user name is ALL lower case. This is reflected also in the error message you provided: "... _**M**_endo".
So try again and type the user name ALL lower case.

If that still doesn't work, you can try to connect locally on the Ubuntu machine (meaning, install NX Client for Linux from [http://nomachine.com](http://nomachine.com) and try to connect to 'localhost'). This will eliminate the possibility of any network problems, and if doesn't work it will be either wrong username/password or NX server not installed properly and not working.

I have done this installation dozens of times and it is a very stable piece of software. The only times I encountered a similar error like you was in fact when the username was typed with the first letter capitalized.

Notice by the way, that on any first connection to a new machine, it will offer you to save an authentication key. This is done so in future if the host IP changes, it will worn you before connecting (in case it was hacked).

Let us know how it went.

---

### Post by cybergalvez on 2012-09-01
X2go is also a very good and easy solution

---

