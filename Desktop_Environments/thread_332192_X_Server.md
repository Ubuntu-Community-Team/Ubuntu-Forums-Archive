---
title: "X Server"
date: 2007-01-05
forum: Desktop Environments
---

### Post by gmanigault on 2007-01-05
I have Ubuntu setup on two systems.  One is a laptop and the other is a server.  On the laptop the system boots into graphics mode.  The server on the other hand only boots up in text mode.  I understand the runlevel stuff but that doesn't seem to make a difference.  Can anyone point me in the right direction to do some reading to put this box in graphic mode from text?  

Thanks.

---

### Post by meng on 2007-01-05
The Ubuntu server edition does not come with a graphical desktop by default. You can add one if you wish. The reason is that many servers don't NEED a graphical desktop (many don't even have a monitor) and in addition, having a fully-featured desktop with lots of applications can encourage you to do things like websurfing which isn't really appropriate for a server (at least not if you're paranoid about security).

If you want to install a graphical desktop, then consider:
sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-dekstop
(You only need one of these)

Perhaps you could tell us what you need to do with the server. Maybe you installed server when what you REALLY wanted was a workstation.

---

### Post by kidders on 2007-01-05
Oops! Too slow.

[COLOR="Silver"]Hi there,

Ubuntu's server edition doesn't come with an X server installed out of the box. I imagine they presumed it would be a waste of disk space & CPU time.

You can "apt-get install" X if you want to, but if you do that, you might as well have installed a desktop release, I'd say.[/COLOR]

---

### Post by gmanigault on 2007-01-05
If I am the only one running the server it is in my house okay.  Another question.  That is okay if I don't use it in graphic mode but how do I get and install packages like firestarter (firewall) which is graphical.  I keep getting and error when I try the sudo apt-get firestarter

Thanks. 

> **meng said:**
> The Ubuntu server edition does not come with a graphical desktop by default. You can add one if you wish. The reason is that many servers don't NEED a graphical desktop (many don't even have a monitor) and in addition, having a fully-featured desktop with lots of applications can encourage you to do things like websurfing which isn't really appropriate for a server (at least not if you're paranoid about security).

If you want to install a graphical desktop, then consider:
sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-dekstop
(You only need one of these)

Perhaps you could tell us what you need to do with the server. Maybe you installed server when what you REALLY wanted was a workstation.

---

### Post by kidders on 2007-01-05
Most of the apps you're used to running are often only front-ends to interface-less utilities that underly them. In firewall terms, **apt-get install iptables** is what you want, I'd say.

---

