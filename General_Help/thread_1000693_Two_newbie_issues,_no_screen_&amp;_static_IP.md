---
title: "Two newbie issues, no screen &amp; static IP"
date: 2008-12-03
forum: General Help
---

### Post by daniel_owen_uk on 2008-12-03
Ok I have two issues, my ubuntu box sits under the stairs, has no screen, does a few things upnp, sabnzbd, file sharing etc.

Problems I have, since the move to intrepid, it won't boot without a screen, no idea why, put a screen on it, everything is fine and dandy.

Static IP, won't let me use the gui, some error message I can't remember, I set the file, etc/network/interfaces to look how it should;

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

Anyone provide any help?

---

### Post by jgoguen on 2008-12-03
What happens with your /etc/network/interfaces set up the way you have it?  Simply nothing?  Does it use DHCP anyway?  I'm not sure you need the 'network' line, but it shouldn't hurt.  Try making the eth0 block in your interfaces file look like this:

```
auto eth0
iface eth0 inet static
     address 192.168.0.100
     netmask 255.255.255.0
     broadcast 192.168.0.255
     gateway 192.168.0.1
```

The reset the interface:
```
sudo ifdown eth0
sudo ifup eth0
```

The reason it won't boot with no monitor, IIRC, is because X now dynamically configures itself, which involves asking the monitor for its supported resolutions.  I don't know how to change that though.

---

