---
title: "Server with desktop environment not networking?"
date: 2011-08-16
forum: Desktop Environments
---

### Post by SublimeBuntu on 2011-08-16
Hey,
At my job we have a setup where computers need to be mirrors of our server for local development, but also need to be usable for those who are less technically inclined. For this I was told to install the server version 10.04 LTS onto the computers and then slap the desktop environment ontop so that everything is setup for everyone. It works fine behind a router that is already registered on the network, but the connection is not but the connection does not show up in the network manager and when plugged directly into the network no DHCP offers are given. On top of that, when we try to register the computers when directly connected to the network, the registration script returns that the MAC address is not present on the network.

The /etc/network/interface file looks like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Even though the interface is not managed, as long as the computer is plugged into the router, everything works, but we need the computer to be connected to the outside world without port forwarding on the router.

Any ideas? I find it most intriguing that I get no DHCP offers nor is my MAC visible on the network...

---

