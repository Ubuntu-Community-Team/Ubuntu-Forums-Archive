---
title: "I have to keep asking"
date: 2005-12-18
forum: General Help
---

### Post by linrasta on 2005-12-18
Either no one knows anything about it, or no one is responding, so I have to keep asking:

I have a computer with 2 network cards.  One for DSL connection coming in, the other out to the network to share the internet.  My ubuntu configs via DHCP, but I want to run also DHCP services to the rest of the network.  I installed the dhcp server from the repositories (multiple versions) and I used the firestarter firewall wizard to try and configure it.  The firewall runs fine, but when it tries to start dhcp services it fails.  even If i try to start dhcp manually, it fails.  it says i need a subnet declaration for eth1 (connection to the network).  Any ideas on what to do?  How do I make a subnet declaration, and what do I do if that doesn't fix the problem.  Thanks.

---

### Post by tuxy on 2005-12-18
If its a small home network why don't you use static IP addresses? It will solve your problem because you can enter everything manually.
 
OR you can leave your eth0 as DHCP and eth1 as static. Get into /etc/network/interfaces and for eth1 enter the following:

auto eth0
iface eth0 inet static
address 192.168.1.120
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1

Since Ubuntu is a Debian based distro it gives the router/gateway as 192.168.1.1 by default. Once you have entered the above data. Do *ifdown -a* and *ifup -a* or cd /etc/init.d/./networking restart . You have to do all these as root user!

Let me know how it went :smile:

---

### Post by linrasta on 2005-12-18
eth0 is dhcp, because that is how it gets connected to the internet.  eth1 currently is static, because dhcp won't work for it.  The network is going to be VERY large, so I need dhcp for convenience.  What could I do in this case?

---

### Post by tuxy on 2005-12-18
I wont be much helpful to you I guess:(
Check this link if this might be helpful to you:
[http://www.ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server](http://www.ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server)

---

### Post by linrasta on 2005-12-18
This looks like it might work.  I'll give it a try and let you know.  Thanks a ton!

---

### Post by linrasta on 2005-12-18
Cool! It worked tuxy!  You're awesome!  I searched the forums and I have never seen that post.  Thanks a million!

---

### Post by linrasta on 2005-12-18
I works!  DHCP is working now.  Thanks a ton!

---

### Post by earobinson on 2005-12-19
for the future please if you have to bump the old thread do not make a new thread this just gunks down the forums and makes it so when a user is searching for a soultion me might find your old (now usless thread) instead of the one with the answer.

---

### Post by tuxy on 2005-12-19
[QUOTE=linrasta]I works!  DHCP is working now.  Thanks a ton![/QUOTE]

Nice.:D

---

