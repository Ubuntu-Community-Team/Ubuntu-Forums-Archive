---
title: "Upgrade to 8.10 broke network-manager-openvpn"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kgish on 2008-11-17
I have a Dell Latitude D620 which worked just fine and I could connect normally with my office via VPN.

Unfortunately, once I upgraded from 8.04 to 8.10 it doesn't work anymore. Any network address on the office network I try to connect (e.g. ping) just hangs for awhile before returning an error message.

I heard somewhere that in 8.10 the network-manager was rewritten so was wondering if anyone has had similar problems.

---

### Post by Muflon on 2008-11-19
Hi kgish

Are you using VPNC ?

Muflon

---

### Post by aeg1s on 2008-11-23
network-manager-openvpn is broken for me as well...  For some reason it is messing up the routing tables.  I can get openvpn to work fine from command line though, which confirms it is a network-manager-openvpn issue.  It allows me lan access to the vpn, but any web browsing is broke.

---

### Post by philws on 2008-12-10
I have exactly the same problem - my 8.04 Network Manager's VPN connections using OpenVPN worked a treat, but after upgrading to 8.10 they broke. I'm having to resort to CLI initiation of VPN (with a second command to fix up DNS) which is a real shame (I like how easy Network Manager makes this sort of thing). :(

---

### Post by spotrick on 2008-12-13
I've had this same problem, and also cannot get it to work from command line - just running vpnc. @philws can you share what you do to make it work?

---

### Post by jimikimble on 2008-12-22
I'm having the same issue, also not working from the commmand line, which is how I was connecting in 8.4.

---

### Post by TalynOne on 2008-12-26
The following method should work, and IMO works a lot better than using Network Manager:

[http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

---

### Post by jimikimble on 2008-12-29
I fixed mine by installing openvpn from source. 
[http://openvpn.net/index.php/downloads.html](http://openvpn.net/index.php/downloads.html)
following the instruction in the INSTALL file (I had to download the dev files for a couple of packages during the ./configure step --if you don't have the packages, it will tell you what you don't have and you can find them with your preferred package manager)  

After that was done I still had a problem where /etc/resolv.conf was not a symlink to /etc/resolvconf/run/resolv.conf probably due to playing around with kvpnc  
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/785cddcdfd53dbd6](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/785cddcdfd53dbd6)

But hey, I feel good that I got it working.  :)  Hope this helps somebody.

---

