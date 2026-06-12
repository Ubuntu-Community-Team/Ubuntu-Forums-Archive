---
title: "so tired of this! no internet"
date: 2006-05-22
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-05-22
I have two boxes on in the room im currently in, both used to work just fine, i got interet access on both..

now, only one of them will work..

i try activating the network connection with DHCP, and with a static IP, none of which, gives me any results, I run sudo dhclient eth0, doesnt work eithter.

what the hell is wrong, (cables are hooked up the same way), it worked fine a day ago!

---

### Post by nanotube on 2006-05-22
post output of "ifconfig" ?
also, try "sudo ifup eth0" (sub whatever your interface is for eth0)

---

### Post by stiankarlsen on 2006-05-22
> stian@ubuntustian:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.


stian@ubuntustian:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:39:89:D6
          inet6 addr: fe80::213:d3ff:fe39:89d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3779 (3.6 KiB)  TX bytes:12068 (11.7 KiB)
          Base address:0xcf00 Memory:fdde0000-fde00000

really dont know whats wrong, hope you can spot something? (Im not very familiar with linux in general)

---

### Post by stiankarlsen on 2006-05-23
nobody?

---

### Post by stiankarlsen on 2006-05-25
This is just too weak!

---

### Post by dmizer on 2006-05-25
have you disabled ipv6.

post the content of your /etc/network/interfaces

comments like this:
> This is just too weak!
are much less likely to endear you to the community who is here volunteering their personal (unpaid) time to help.

you have a router.  have you rebooted your entire network?

---

### Post by Zimmer on 2006-05-25
your ifconfig shows no broadcast or mask information...so you need to check the routing (I think). I will look up the relevant commands and get back to you...and the message from your ifup command does not look too healthy, either ...

EDIT:
Try here for a few more pointers as to where the problem is...
[http://ubuntuforums.org/showthread.php?t=180582](http://ubuntuforums.org/showthread.php?t=180582)

---

### Post by stiankarlsen on 2006-05-25
Sorry for taking such a bad tone, i'm just so frustrated. (Won't happen again)

Either way, here's my interfaces file.
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

iface lo inet loopback

iface eth0 inet dhcp

auto eth0


I have rebooted the entire network, but still nothing.

---

### Post by nanotube on 2006-05-25
try following this howto:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by dmizer on 2006-05-25
[QUOTE=stiankarlsen]Sorry for taking such a bad tone, i'm just so frustrated. (Won't happen again)

Either way, here's my interfaces file.


I have rebooted the entire network, but still nothing.[/QUOTE]
believe me i understand the frustration ... lol.

looks like you have two eth0 configured in interfaces.  this is likely the root of your problem.  i was having that same problem earlier.  search in synaptic for network-manager ... if you have it, uninstall it.  then remove the line that says "auto eth0".  reboot, and do an ifconfig and see if you get an ip then.

---

