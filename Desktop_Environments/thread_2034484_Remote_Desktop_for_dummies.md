---
title: "Remote Desktop for dummies???"
date: 2012-07-28
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2012-07-28
Hi All,

I've been looking for instructions regarding the setup and use of the Remote Desktop Viewer software. All the explanations I locate are either badly dated, or written in technobabble-way beyond my ability to understand. 

I want to share desktops across the internet, from Xubuntu to Xubuntu and Xubuntu>Ubuntu Unity.

It seems there was a time in the past when Remote Desktop Viewer came as default with some older versions...but, 3 years old is an eternity and current versions of Xubuntu don't appear to have support for Remote Is there a step by step instruction file for preparing the system for use with Remote Desktop Viewer or x11vnc??
Desktop Viewer.
Is there a step by step instruction file for preparing the system for use with Remote Desktop Viewer or x11vnc??

I also looked at [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/). This is the developer of x11vnc, which might do the same job, but again, I can't understand the instructions he provides as 'notes'.

Note that I will not use Teamviewer as it isn't open source.

Is there a step by step instruction file for preparing the system for use with Remote Desktop Viewer or x11vnc ie:Remote Desktop Viewer for Dummies)??

TY.

Art

---

### Post by Rodney9 on 2012-07-28
I am using Remote Desktop on Xubuntu 12.04, it works well.

Getting the other machine ( I used Crunchbang as I wanted a lightweight music player on an old machine ) was the hardest part, I ended up using VNC Server with a lot of twiddling.

---

### Post by goodbye-windows(tm) on 2012-07-28
Hi Rodney,

I did manage to get Remote Desktop Viewer to log into my daughters laptop that is on our local network, which was Xubuntu to Unity. But, couldn't make the Ubuntu to Xubuntu (reverse path) work no matter what i did.

Accessing it via the internet was impossible, for some reason. I did learn that  had to open some ports in our router, but by then I had already given up and uninstalled.

What did you do to make your connection work across the internet? And, where did you find the instructions to do it? 

Also, how did you enable the Xubuntu computer to allow incoming connections?? All the examples given give instructions for enabling incoming connects if the computer is running Unity. And, Xubuntu doesn't have the programs necessary to enable incoming connects. 

Appreciate any nudges in the right direction that you can provide.

Regards,

Art

---

### Post by asmoore82 on 2012-07-28
> **goodbye-windows(tm) said:**
> I want to share desktops across the internet

There's all sorts of security implications there. It's much safer to remote within a local network only. Which is to say that all the same security implications exist on the local network; but it's not as risky to ignore them.

So the correct answer is always mildly complicated, but I would recommend any of tightvncserver/tigervncserver/x11vnc but always in combination with SSH and secure port forwarding.

Also, there are 2 major completely different "styles" of VNC. x11vnc is for "breaking in" to a pre-existing GUI session that is already attached to a physical monitor. tight or tiger vncserver can create an "invisible" GUI session that is only available remotely. Both "styles" have pros and cons. tight or tiger vncserver sessions can never fail due to graphics driver issues or graphics hardware failure. But sometimes you left a program running on your physical screen and really need to get at it, so x11vnc is your only option.

---

### Post by QIII on 2012-07-28
See the Community Wiki [here]("https://help.ubuntu.com/community/VNC").

Absolutely, definitely, without fail -- use SSH over the internet.  You will have to use port forwarding on your router.  I would use a non-standard port and DO NOT use an SSH password, but a public/private key combination.  Use at least a 2048 bit key.  Additionally, use something like DenyHosts to monitor connection attempts.

Because most ISPs do not provide fixed IP addresses to residential users, you will have to subscribe to a dynamic DNS service to reach your home computer.  The services are inexpensive, on the order of $20 annually.

In my opinion, NX technology is far superior to VNC.  It provides performance on par with Microsoft's RDP and is well optimized to low-bandwidth, high-latency connections.

---

