---
title: "After system boot, eth0 is up but has no ip"
date: 2006-08-16
forum: Desktop Environments
---

### Post by do77 on 2006-08-16
my env:
ubuntu 6.06

my config:
All is OK,
and eth0 in /etc/network/interfaces:
auto eth0
iface eth0 inet dhcp

description:
After system boot, eth0 cannot get IP though dhcp.
But if I ifdown eth0 & ifup eth0, then I can get IP.
Then I check my /etc/rcS.d/, find in /etc/init.d/networking, when "ifup -a", the eth0 has already up(but do not get IP), so /etc/init.d/networking do nothing.
then I find in /etc/init.d/udev, when run "udevplug", eth0 is up without IP.

I find when system is booting, after /etc/rcS.d/S10udev run, the 2 thead is appeared and keep exist.
root 2322 1 0 22:24 ? 00:00:00 /sbin/ifup --allow auto eth0
dhcp 2382 2322 0 22:24 ? 00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

Please tell me why I have this problem,
Should udevplug make eth0 up?
Or This is a bug of ubuntu?

---

### Post by murataht on 2006-08-17
i got a wifi interface, that using the neighbour's wifi. sometimes, my eth1 up with ip address, sometimes without an ip address. i was thinking this should be a access range problem. and i deactivate and activate the eth1 to get an ip. maybe this is the same problem as yours. i would like to know how to fix it too.

btw, i read a post couple of minutes ago, it addresses a very similar problem. 
[http://www.ubuntuforums.org/showthread.php?t=237427](http://www.ubuntuforums.org/showthread.php?t=237427)

hope someone notice this, and give a good suggestion.

---

### Post by do77 on 2006-08-18
I find when system is booting, after /etc/rcS.d/S10udev run, the 2 thead is appeared and keep exist.
root 2322 1 0 22:24 ? 00:00:00 /sbin/ifup --allow auto eth0
dhcp 2382 2322 0 22:24 ? 00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

---

### Post by pt123 on 2006-08-19
You might want to try the solutions mentioned on these threads:

[http://ubuntuforums.org/showthread.php?p=1398949#post1398949](http://ubuntuforums.org/showthread.php?p=1398949#post1398949)

---

