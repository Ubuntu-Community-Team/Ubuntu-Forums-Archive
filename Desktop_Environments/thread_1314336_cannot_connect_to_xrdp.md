---
title: "cannot connect to xrdp"
date: 2009-11-04
forum: Desktop Environments
---

### Post by tlyczko on 2009-11-04
I have an Xubuntu 9.10 Karmic Koala VM set up within VMware ESX to test out xrdp.

xrdp appears to appropriately start up when Xubuntu is booted.

When I try to RDP to the VM (it has a DHCP address), I get the following messages:

connecting to sesman ip 127.0.0.1 port 3350
sesman connect ok
sending login info to sesman
login successful for display 10
started connecting
connecting to 127.0.0.1 5910
error - problem connecting

What can I do to fix this??

I really don't want to deploy other VNC servers/clients etc., I would really like people to be able to use Windows RDP...

I opened 5910 in the Xubuntu VM's firewall for both TCP/UDP via gufw.

I could also use xdmcp but I cannot find anything on how to enable this in Xubuntu 9.10.

Thank you, Tom

---

### Post by tlyczko on 2009-11-04
got this solved.

I had to remove xrdp, vnc4server, tightvnc, which were all installed in the wrong order.
 
I had to install tightvncserver, then install xrdp.
 
Please see: 
[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/375755](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/375755)
[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/220005](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/220005)

It's important to do tightvnc before xrdp.

Doing things in this manner will cause xrdp to use tightvncserver instead of vnc4server, which will not work.

I'm not a Linux expert.

Thank you, Tom

---

