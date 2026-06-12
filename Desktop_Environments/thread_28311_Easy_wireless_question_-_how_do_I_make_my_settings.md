---
title: "Easy wireless question - how do I make my settings automatic?"
date: 2005-04-19
forum: Desktop Environments
---

### Post by epb613 on 2005-04-19
When my computer boots up, ipw2200 is automatically loaded and recoginsed.

To log on to my network, I type:

sudo iwconfig eth1 essid Gr33nG0bl1n
sudo iwconfig eth1 key restricted DA1608B7C9
sudo /sbin/dhclient

And then I'm ready to go. I wanted to know though if there's a way to have this automatically configured during /etc/init.d/networking during bootup.

My /etc/network/interfaces file looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
 script grep
 map eth0

# The primary network interface
iface eth0 inet dhcp


What do I have to add to it? Thanks alot in advance!

---

### Post by Takis on 2005-04-19
Why not create your own init.d file? 

[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)

---

