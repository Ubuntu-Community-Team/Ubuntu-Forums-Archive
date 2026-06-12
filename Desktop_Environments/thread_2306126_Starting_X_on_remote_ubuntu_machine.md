---
title: "Starting X on remote ubuntu machine"
date: 2015-12-12
forum: Desktop Environments
---

### Post by Krishna_Srihasam on 2015-12-12
Hi,

 I am a newbie and would like some help on a problem which I am facing.  Here is my scenario:

I have several linux computers connected touch screens in a experiment setup. I want to remotely start those machines from a centralized place ( say, some other room) and I want to start my program which launches a X session on each machine on the touchscreen monitor.

I currently have a solution based on slackware linux, but I want to move to ubuntu (because of obvious reasons). 

I am having trouble to start an X session on a screen connected to this ubuntu computer remotely.

Any suggestions/ideas/help is more than welcome

-Krishna

---

### Post by matt_symes on 2015-12-12
Hi
> **Krishna_Srihasam said:**
> Hi,

 I am a newbie and would like some help on a problem which I am facing.  Here is my scenario:

I have several linux computers connected touch screens in a experiment setup. I want to remotely start those machines from a centralized place ( say, some other room) and I want to start my program which launches a X session on each machine on the touchscreen monitor.

I currently have a solution based on slackware linux, but I want to move to ubuntu (because of obvious reasons). 

I am having trouble to start an X session on a screen connected to this ubuntu computer remotely.

Any suggestions/ideas/help is more than welcome

-Krishna

To wake the PCs then wakeonlan (to wake up when a magic packet is sent) or rtcwake (to wake up at a specific time if your BIOS supports it) spring to mind.

If the network is *secure* then xdmcp will work for remote desktop. There's also vnc, or a secure variant, or x2go client and server for a remote desktop.

Can you explain in detail, what was your setup under Slackware ?

Kind regards

---

### Post by ian-weisser on 2015-12-12
There are several methods.
X in Ubuntu is started by lightdm, which runs the local GUI login screen.

One is to ssh from the client to the server and start X manually, then launch VNC/RDP/whatever X-sharing software. Remember to use a secure method of sharing the X session!

Another is to use ssh's -X flag, and not use X on the target machine at all.

Yet another is to use lightdm's 'login to a remote session' GUI option, which will try to launch X on the remote system.

---

