---
title: "100% wifi signal but not internet?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by Simian on 2005-09-29
I entered my essid and wep key. A wifi applet says "Eth1:link quality 100%, bitrate 11Mbits". So I've done something right (I think) but when I load Konqueror or "sudo apt-get update" there is clearly con connection.

I suspect (prey) it's probably something quite simple.

I would be so grateful if anyone could point me in the right direction.

---

### Post by grinchy on 2005-09-29
try sudo dhclient eth1

---

### Post by shakin on 2005-09-29
[QUOTE=grinchy]try sudo dhclient eth1[/QUOTE]

And if that doesn't work, maybe your DNS servers aren't being added to resolv.conf.

Try: 'ping 216.239.37.99' and see if you get a response. You can also browse to that IP: [http://216.239.37.99](http://216.239.37.99) (it'll take you to Google).

If you can use the IP, but not the domain, find your DNS server from Windows, or you may be able to use your router's IP address, and add it/them to /etc/resolv.conf.

Eg.
nameserver 192.168.1.1

---

### Post by Simian on 2005-09-29
[QUOTE=grinchy]try sudo dhclient eth1[/QUOTE]

Ok it comming up with DHCPDISCOVER on eth1 ....

what will this do?

---

### Post by Simian on 2005-09-29
sudo dhclient eth1 resulted in no working leases in persistant database - sleeping

and ping 216.239.37.99   connect: network unreachable

---

### Post by Simian on 2005-09-29
sorry if I sound like a moron but I think that my router IP addres is 192.168.0.2

so do I add    nameserver 192.168.0.2
or my essid 192.168.0.2

to /etc/resolv.conf

---

### Post by audax321 on 2005-09-29
Can you post /etc/network/interfaces (obviously convert your WEP key and ESSID to XXXXX or something). I had a similar problem with my laptop and basically KDE just wasn't configuring that file properly. Editing manually fixed it.

---

### Post by shakin on 2005-09-29
[QUOTE=Simian]sorry if I sound like a moron but I think that my router IP addres is 192.168.0.2
so do I add    nameserver 192.168.0.2
or my essid 192.168.0.2
to /etc/resolv.conf[/QUOTE]

You'd put 'nameserver', but don't worry about it. If you can't ping an IP then this isn't your problem. Or at least it's not your biggest problem. Do what audax321 asked and post your interfaces file. This is probably where the problem is. Just yesterday on a Debian box I was getting "Network not reachable" and I had to fix it in the interfaces file (I forgot to put in the gateway!)

---

### Post by Simian on 2005-09-29
Below is my,   vi /etc/network/interfaces



 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid MonkeyNet
wireless-key s:***************************

auto eth1


Thanks for your help...

---

### Post by audax321 on 2005-09-29
Your /etc/network/interfaces file looks fine. I'm just not sure about one thing. Why is there a s: infront of your wireless-key?

Try changing it to this form:
  wireless-key ##################
with no s: in front of it. Unless of course your using WPA or something in which case I could be wrong because I don't have much experience with it.

---

### Post by Simian on 2005-09-30
[QUOTE=audax321]Your /etc/network/interfaces file looks fine. I'm just not sure about one thing. Why is there a s: infront of your wireless-key?

Try changing it to this form:
  wireless-key ##################
with no s: in front of it. Unless of course your using WPA or something in which case I could be wrong because I don't have much experience with it.[/QUOTE]


It worked. **Thank you **so much audax321. I've been trying to fix that since last Sunday.

Thanks to everyone else for your efforts. :smile:

---

