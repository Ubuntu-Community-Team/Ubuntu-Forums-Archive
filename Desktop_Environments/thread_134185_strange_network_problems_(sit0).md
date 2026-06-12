---
title: "strange network problems (sit0)"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jeroen_ter_heerdt on 2006-02-21
Hi,

I found a rather strange problem.
I've got my ubuntu box with a 3com ethernet card.
This card is properly recognized, and I can use it and configure it. I'm also allowed to do anything (as I'm using it right now).
But (there's always a but) this is when I use dhcp to get my IP. i.e. my /etc/network/interfaces lists:
---Start of exert of interfaces---
[FONT="Courier New"]iface eth0 inet dhcp
netmask 255.255.255.0
dns-nameserver 192.168.2.1[/FONT]
---End of exert of interfaces---

But, when I want to use a static IP (for example for being able to connect remotely) I will get the right IP, but for some reason this is lost after for example a reboot, or just after logging out logging in.
My /etc/network/interfaces lists then:
---Start of exert of interfaces---
iface eth0 inet static
address 192.168.2.111
netmask 255.255.255.0
gateway 192.168.2.1
---End of exert of interfaces---

The strange thing is when I do: ifdown eth0 and ifup eth0 this line appears twice:
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776

This is when I'm using a DHCP IP off course. Still, I get the IP because the whole listing is like:
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:04:76:17:89:cf
Sending on   LPF/eth0/00:04:76:17:89:cf
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.111 -- renewal in 1006937237 seconds.

So, basically my interface works (with DHCP) and seems to work with static IP, but after some time/reboot/login-logout it doesn't do it anymore (with static IP).

I've switched interfaces, but that didn't help.

Any ideas? :confused: 

Regards,
Jeroen ter Heerdt

---

