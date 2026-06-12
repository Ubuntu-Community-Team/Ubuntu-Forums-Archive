---
title: "Trying to enable ethernet"
date: 2005-04-23
forum: Desktop Environments
---

### Post by UbuntuNewb on 2005-04-23
Okay I just about gave up on getting my wireless card to work.  I tried ndiswrapper etc.  So now I'm trying to get my ethernet to work.  Everything seems okay and then I click enable interface in the control center and it says Enabling interface eth0 waits like a full two minutes and then does nothing.  Is there a place I can view any errors that might be happening?

I'll post my configuration file and see if that's any help to the more veteran users here.

```
# This file describes the network interfaces available on your system.
# and how to active them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
             script grep
             map eth0

iface eth0 inet dhcp

```

---

### Post by heimo on 2005-04-23
Open terminal and run *tail -f /var/log/messages *
Open another terminal and run [i]sudo /etc/init.d/networking restart
[/i]
Watch the first terminal. 

Run *ifconfig eth0* you should get information about configured interface
Run *sudo /sbin/dhclient *(runs the dhcp request)

---

