---
title: "vmware slow under linux"
date: 2008-12-12
forum: General Help
---

### Post by asearle on 2008-12-12
I have an ASUS z92 with 2gb of RAM dual booting windows xp and Ubuntu and with VMWare Player installed on both OS's.

In both cases VMWare works fine and I can open up my virtual machines.  But under Windows everything is MUCH faster.

This is all a bit frustrating because the whole point for me is to be able to do away with Windows and work with VMWare under Linux.  But the slow speed is a big problem.

I have tried a full version of VMWare under Linux but the speed is just the same.

My question is whether this is simply 'The Nature of the Beast' (i.e. VMWare is slower under Linux)?  Or whether there are some settings that I can change to get the speed up a little?

Many thanks for any tips that you can give me or any pointers to good HOWTOs.

Cheers and thanks,
Alan Searle

---

### Post by ju2wheels on 2008-12-12
I would honestly recommend using VirtualBox over VMWare. Its orders of magnitude faster than VMWare, regardless of which OS is the host. It supports loading VMWare images, but for full performance benefits I would also suggest using VirtualBox's image format.

---

### Post by asearle on 2009-01-25
Many thanks for the tip and, yes, Virtual Box looks great:  It installed much more easily than VM-Ware and seems to have great functionality and excellent speed.

The only problem that I have is that it seems to be stuck on a very low resolution (800x600) and so I was wondering whether you have any tips for bumping that up a little?  Do I need to install the graphics drivers for my particular graphics card?  Or does Virtual Box handle graphics itself?

Many thanks,
Alan Searle

---

### Post by xc1024 on 2009-01-25
you need to have your virtual OS able to handle resolutions more than that. alos try installing vbox additions on virtual machine, it may help you.

---

### Post by ju2wheels on 2009-01-25
> **xc1024 said:**
> you need to have your virtual OS able to handle resolutions more than that. alos try installing vbox additions on virtual machine, it may help you.

+1. Yes you need to install graphics drivers on the guest machine (the machine running inside virtualbox. This is done by installing Virtualbox "Guest Additions" which installs custom video, mouse, and ethernet drivers designed to all Virtualbox to dynamically control the mouse and video resolution.

---

