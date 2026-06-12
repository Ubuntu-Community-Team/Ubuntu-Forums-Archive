---
title: "[B]Little Niggle Connecting to the net[/B]"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Q4U on 2006-03-01
Hi:

I installed Kubuntu on my laptop, everythings looks fine, except for a small thing.

In order to get online at the beginning of each session, I have to type in the terminal

$ sudo ifconfig eth0 up
$ sudo dhclient

I'd like to get online automatically as I switch on the laptop.

dante@inferno:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping eth0
        script grep
        map eth0

Also, my routing table (route -n) at startup is empty.:confused: 

I have a Toshiba ultra-portable (those with the eth0 in a port replicator) and connect to a wired router. The local dhcp server is enabled.

Any help appreciated. Q4U

---

### Post by ltmon on 2006-03-01
<guess>You could try putting 'auto eth0' in your /etc/network/interfaces</guess>

L.

---

### Post by Q4U on 2006-03-01
Unfortunately it did not work. I tried commenting the eth0 stuff, as well, but the result did not change.

Well, for now I have added an icon to my desktop connecting to a little script that does this automatically. I have also another icon for the wireless, which is quite handy. So I am not overly bothered by this quirk.

Thanks anyway

PS Great avatar, I am listening to Kind of Blue right now (well, the live version in Copehagen)

---

### Post by Q4U on 2006-03-02
Solved! 

Just went to KControl and configured it from there. In the Internet and Networking there is an option for hooking up to the network at startup. Similarly, I configured the default gateway manually from there.

Why this was not done during installation I don't know, but it was not too difficult to sort out. :D 

Q4U

---

