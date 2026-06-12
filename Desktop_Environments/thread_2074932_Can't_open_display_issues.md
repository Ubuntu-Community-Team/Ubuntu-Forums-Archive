---
title: "Can't open display issues"
date: 2012-10-22
forum: Desktop Environments
---

### Post by yairz on 2012-10-22
Hi all,

I am fairly new to Ubuntu but have some experience with RHEL.

I need to set up a new environment with an RHEL 5.8 server and two Ubuntu 12.04 LTS desktops.

As part of the work on this environments, users from the Ubuntu desktops should connect with SSH to the server and run an X application which will open on their desktop.

So far I have configured SSH to allow X11 Forwarding on both ends (sshd_config and ssh_config), ran xhost + on both server and desktops and mapped the DISPLAY on the server to the desktop.

However,when I run the following commands on the desktop I get the following error:

$ export DISPLAY=MyUbuntuIP:0
$ xclock
Can't open display MyUbuntuIP:0
$ xhost +
Unable to open display MyUbuntuIP:0

I checked permissions on .Xauthority files, everything looks fine, the firewall configuration is set to accept any connection (I have not found any application to manage the firewall).

Any advice would be much appreciated.
Thanks,
Yair

---

### Post by rbruceporter on 2012-12-30
I had similar issues until I added the following directive to the /etc/ssh/sshd_config file:

X11Forwarding yes
X11DisplayOffset 10
X11UseLocalHost no

The first two options were already there, the 3rd option was the one that fixed everything for me. Check man sshd_config for more info.

Hope this helps.

Robert

---

