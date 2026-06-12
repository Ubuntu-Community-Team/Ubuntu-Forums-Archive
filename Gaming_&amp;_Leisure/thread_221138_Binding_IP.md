---
title: "Binding IP"
date: 2006-07-22
forum: Gaming &amp; Leisure
---

### Post by TotalinkGameServers on 2006-07-22
Hello everyone, 

I am running a MOHAA game server.  I will be setting up many servers, and some for free public use.  Counter-Strike, Medal of Honor Spearhead and many more.  I am first testing on my box at my house.  Its not very powerful, but I will be moving powerful linux boxes to DS3 connections. Anways, for anyone who can help me, if they are interested in a free game server.  

Ok, I run as a normal user (not sudo) : ./mohaa_lnxded +exec server.cfg

(it doesnt matter if I run sudo or even under root, still the ip doesnt bind)

And it sets up, but this is my problem.  Binding IP addresses.  My nic card has the IP address of 192.168.1.100.  My router has the ports 12200 through 12240 directed to 192.168.1.100 and i even tried DMZ.  Still it gives me this error:

You are now setup for easy mode.
Opening IP socket: 24.210.214.147:12203
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12204
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12205
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12206
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12207
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12208
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12209
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12210
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12211
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
Opening IP socket: 24.210.214.147:12212
ERROR: UDP_OpenSocket: bind: Cannot assign requested address
ASSERT: [qcommon/common.c:406] Couldn't allocate IP port (fyi)
Error: Couldn't allocate IP port

I've found /etc/network has all my network information.  the "interfaces" file contains this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


Can anyone help me so I can have the MOHAA dedicated server to my  external IP rather than just the internal IP of the nic card.  Thanks!

---

### Post by Waste on 2006-07-23
Are you trying to bind it to your external IP?
If you are, you know you don't have to do that.

---

