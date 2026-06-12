---
title: "Cannot get internet after instaling CAE LINUX (UBUNTU) on OPTPLEX 760"
date: 2010-01-22
forum: Desktop Environments
---

### Post by didospear on 2010-01-22
Hi

I am trying to install Linux on a PC (Dell OPTIPLEX 760) with an Intel Corporation 82567LM-3 Gigabit Network Connection card.
The problem is I cannot get network connection after installation. when I click on the network status icon on the monitor, it shows "No network devices have been found" 

Then I try check few things or commands and get the following outputs:

$lshw -C network

 *-network UNCLAIMED               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

One can realize that the above output miss a lot of information like: 

logical name: eth0
serial: 00:21:70:e6:ed:88

and even the on the configeration there should be other information like: broadcast, driverversion etc.

I then tried to edit the /etc/network/interfaces file from this:

auto lo
iface lo inet loopback

To this:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

But when I restart the network using: sudo /etc/init.d/networking restart

I get this:

  * Reconfiguring network interfaces...
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhcient.etho.pid with pid 0
Internet System Consortium DHCP Client v3.0.6
Copyright 2004-2007 Internet System Consortium.
All rightd reserved

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0

Then I saw some suggestion about a different problem to install bridge utils using command:

sudo apt-get install bridge-utils

But I get

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bridge-utils

Another suggestion from a different problem, apparently was to solve the "eth0" absence was to modify the 

etc/udev/rules.d/70-persistent-net.rules

by removing from the file, the lines containing:
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="##:##:##:e#:ed:##", AME="eth0"

where # is a number

BUT in my case, the file 70-persistent-net.rules does not even exist rather is not generated. Or anyfile with persistent-net.rules is not there at all.

Any suggestion what I need to do. I must say that when isntalling exactly the same package (caeLinux) on a laptop and onother PC (not a dell) it works perfactly and fine.

Thanking you in advance

---

