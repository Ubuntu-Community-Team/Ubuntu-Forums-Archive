---
title: "VNC when user is not logged in??"
date: 2011-09-16
forum: Desktop Environments
---

### Post by jimerman on 2011-09-16
This is driving me crazy.  It seems I have 2 options using VNC to connect to an Ubuntu box:
b) connect to a logged-in user's desktop, or
c) connect to a special reserved desktop just for the VNC session.

Whatever happened to option:
a) Connect to the computer - whatever is on the screen, be it the login prompt or a user's desktop?

That's what I'm used to with Windows, and often times if a server reboots, I still want to be able to connect remotely to administer it.

Isn't there some technology, be it VNC or not, that will work?  I have tried the built-in desktop sharing, x11vnc, tightvnc, vnc4server (I think that's what, plain vanilla Real VNC?).  What else is there?

---

### Post by haqking on 2011-09-16
> **jimerman said:**
> This is driving me crazy.  It seems I have 2 options using VNC to connect to an Ubuntu box:
b) connect to a logged-in user's desktop, or
c) connect to a special reserved desktop just for the VNC session.

Whatever happened to option:
a) Connect to the computer - whatever is on the screen, be it the login prompt or a user's desktop?

That's what I'm used to with Windows, and often times if a server reboots, I still want to be able to connect remotely to administer it.

Isn't there some technology, be it VNC or not, that will work?  I have tried the built-in desktop sharing, x11vnc, tightvnc, vnc4server (I think that's what, plain vanilla Real VNC?).  What else is there?


For administering a Server (where no DE or GUI should be installed) then ssh is the tool  of choice.

If you must use GUI then you can ssh -X but that depends on X forwarding and the gui apps being installed remotely for use on the X loopback locally.

I dont use VNC so not not sure where that option is for Linux based VNC

---

### Post by jimerman on 2011-09-16
> **haqking said:**
> For administering a Server (where no DE or GUI should be installed) then ssh is the tool  of choice.

Yes, I did install ssh.  However, I should add what I am calling my server is actually Ubuntu desktop.  I have my Windows AD server running in a VM on that machine (it is much more stable as a host than Windows).  I also have a VPN server on an Ubuntu desktop box.  So, I'd prefer to be able to remote into the GUI and jump to a command line if needed, but still do GUI stuff as I am not familiar enough with Ubuntu and don't want to jump to Google for everything;).

> If you must use GUI then you can ssh -X but that depends on X forwarding and the gui apps being installed remotely for use on the X loopback locally.

I dont use VNC so not not sure where that option is for Linux based VNCFound [this page about VNC servers.]("https://help.ubuntu.com/community/VNC/Servers")

I should add - my kids' machines are also Ubuntu, so these are the ones where I may want to connect and help them out (e.g. when I am traveling), or log in and administer (but I choose 1 or the other, either log in while they are logged in, or log into an Admin desktop).

---

### Post by haqking on 2011-09-16
> **jimerman said:**
> Yes, I did install ssh.  However, I should add what I am calling my server is actually Ubuntu desktop.  I have my Windows AD server running in a VM on that machine (it is much more stable as a host than Windows).  I also have a VPN server on an Ubuntu desktop box.  So, I'd prefer to be able to remote into the GUI and jump to a command line if needed, but still do GUI stuff as I am not familiar enough with Ubuntu and don't want to jump to Google for everything;).

Found [this page about VNC servers.]("https://help.ubuntu.com/community/VNC/Servers")


So you want to administer the VM ? then you can do that directly without ssh to your UBuntu host, if the VM is bridged with its own IP ?

and yeah i know what VNC is, used it alot on a LAN for desktop support, i meant i dont use it for remote admin (server admin) on Linux,. so dont know why that option you refer to is not there is what i meant ;-)

---

### Post by jimerman on 2011-10-19
Actually, the administration activities are regardless of the VM.  I am fine with managing the VM through the web interface.  I need to do standard Gnome GUI stuff remotely.  VNC means I have to leave myself logged in - so if the power goes out an the machine reboots while I am not home, I am hosed (other than SSH, which I am not enough of a Linux geek to get by on command line alone).

---

### Post by haqking on 2011-10-19
> **jimerman said:**
> Actually, the administration activities are regardless of the VM.  I am fine with managing the VM through the web interface.  I need to do standard Gnome GUI stuff remotely.  VNC means I have to leave myself logged in - so if the power goes out an the machine reboots while I am not home, I am hosed (other than SSH, which I am not enough of a Linux geek to get by on command line alone).

then like i mentioned before ssh -X which allows you to run the remote GUI apps locally from your own X server.

---

