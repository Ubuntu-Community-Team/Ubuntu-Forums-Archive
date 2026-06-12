---
title: "Ubuntu 8.10 Static IP bug"
date: 2009-01-18
forum: General Help
---

### Post by Arukas on 2009-01-18
I here there's a bug in setting a static IP in Ubuntu 8.10.  I was looking for the work around, does anyone know where to find it? or is it fixed?

---

### Post by mssever on 2009-01-18
> **Arukas said:**
> I here there's a bug in setting a static IP in Ubuntu 8.10.  I was looking for the work around, does anyone know where to find it? or is it fixed?
You need to be more specific. I run two Intrepid machines on static IPs and have no problems.

---

### Post by The Cog on 2009-01-18
You can use these files as examples as how to configure static IP addresses:

**/etc/network/interfces**
> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1


**/etc/resolv.conf**
> nameserver 192.168.0.1


I have heard that thr Intrepid network manager (package gnome-network-manager) interferes with static IP configuration. On checking, I find that the machine with static address doesn't have gnome-network-manager installed, so if your static address keeps getting stomped on, try removing gnome-network-manager.

---

### Post by mssever on 2009-01-18
> **The Cog said:**
> I have heard that thr Intrepid network manager (package gnome-network-manager) interferes with static IP configuration. On checking, I find that the machine with static address doesn't have gnome-network-manager installed, so if your static address keeps getting stomped on, try removing gnome-network-manager.
That tool is pretty much unnecessary these days, anyway. On one of my machines, I use NetworkManager to configure a static IP for my wireless connection, but only on my network. If I join another wireless network, NM uses DHCP. This is an awesome new feature introduced in Intrepid.

---

### Post by Arukas on 2009-01-18
Well, I am setting up a gateway.  And someone I know already did the same thing.  But they said there was a static ip bug in ubuntu 8.10 and there was a work around.  

I haven't gotten to the static ip address part, as I am still reading the documentation.  Was trying to figure what the problem was so I don't get hung up and thinking I did something wrong.

---

### Post by mssever on 2009-01-18
> **Arukas said:**
> Well, I am setting up a gateway.  And someone I know already did the same thing.  But they said there was a static ip bug in ubuntu 8.10 and there was a work around.  

I haven't gotten to the static ip address part, as I am still reading the documentation.  Was trying to figure what the problem was so I don't get hung up and thinking I did something wrong.
"A static IP bug" is too vague to be useful. Just keep going, and if you hit a problem you can't solve, you can ask (providing details, of course).

---

