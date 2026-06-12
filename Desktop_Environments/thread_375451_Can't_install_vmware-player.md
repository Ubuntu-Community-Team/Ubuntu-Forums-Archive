---
title: "Can't install vmware-player"
date: 2007-03-03
forum: Desktop Environments
---

### Post by bpont on 2007-03-03
When I tried installing vmware-player, I get the following errors (I should also mention that these errors recur every time synaptic auto-updates, which is very annoying):

Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet xxx.xx.xxx.x/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

---

### Post by openix on 2007-03-04
Hi,

This looks like a depend package has failed to install. You could try removing the player

apt-get remove vmware-player

and reinstall or check for broken dependancies,

apt-get check

and try to remove / reinstall any broken packages listed

I have a VMWare server install guide at [http://www.openix.co.nz/vmware.php]("http://www.openix.co.nz/vmware.php") which you could take a look at.

Good Luck

---

### Post by skroll on 2007-03-04
I just had this problem yesterday.  There were two problems I had:

1. The vmware-player package was installing the wrong kernel modules.  Look at which kernel module package it is installing, and check the version number against your kernel.  Mine was using one version off, when I installed the correct one, I got a step further, as setting up the package worked (didn't complain about the vmnet stuff).  However, then I got to #2:

2. I got an error about libpng0 versioning.  No clue on why, but this fixed it: sudo chmod 777 ~/.vmware/preferences
It seems that vmware player was having a hard time accessing my preferences.  Not sure exactly what the cause of this was, but it fixed everything.

Hope this helps.

---

### Post by sammao on 2007-06-19
I am new to ubuntu. I have this issue with vmware-player.. I do not have a clue how to do this.. 

How do I fix this problem?

Every time i run apt-get to install "what ever" it complains vmware etc.. 

Probing for an unused private subnet (this can take some time)...
...
...
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: fel vid hantering av vmware-player (--configure):
 underprocess post-installation script gav felkod 1

---

