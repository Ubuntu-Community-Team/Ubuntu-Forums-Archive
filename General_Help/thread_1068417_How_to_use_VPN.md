---
title: "How to use VPN"
date: 2009-02-12
forum: General Help
---

### Post by bgk111 on 2009-02-12
Hey all,

 Im thinking this is likely an easy question, but im relativly new to linux (UBUNTU) and I have no idea (My office computers dont allow any non-admins to install anything so I dont know the first thing about it).  So I am trying to log into a vpn server so that I can ssh into my department computers.  I can get all the info I need to put into the vpn (addresses etc), but I cant seem to figure out how to install and use the VPN.  I have done some looking around and It looks like vpnc may be the way I want to go, so I have gone into the terminal and used:

 sudo apt-get install vpnc

But have no idea where to go from here.  When I type vpnc, I just get text, but I want some sort of GUI to use....is this possible?  Am I looking in the wrong place?  Any help would be greatly appreciated, thanks!

-bk

---

### Post by dcstar on 2009-02-13
> **bgk111 said:**
> 
.......
But have no idea where to go from here.  When I type vpnc, I just get text, but I want some sort of GUI to use....is this possible?  Am I looking in the wrong place?  Any help would be greatly appreciated, thanks!

-bk

Actually the **kvpnc** package works 100% for me connecting to my work Cisco VPN.

---

### Post by bgk111 on 2009-02-13
I'll give that a shot when I get home, thanks!  Ill post back with results.

---

### Post by mkarnicki on 2009-02-15
Hi,

I'd like to use vpnc (I'm not fond on using K* aplication on my Gnome ;) ). Could you help me please? I'd like to connect somewhow to my school, the data is provided below, how should I use it with vpnc?

/man vpnc is pretty much, but not that self explanatory for me :< /

(by the way, why Network manager -> VPN is all disabled?)
(data is collected from screenshot tutorials with kvpnc from my institute)

Microsoft PPTP
MPPE necessary
username and password
vpn gate: vpn.pjwstk.edu.pl

routes:
10.0.0.0/8
172.16.0.0/12

I'd really like to use Network Manager VPN tab, but it's all greyed out.. I'll be greatful for help :) .

---

### Post by mkarnicki on 2009-02-15
Replying myself.. I lacked a packet or two concerning PPTP, I can use Network Manager now, but it fails to connecct.. probably just some configuration issue now.

---

### Post by k3rnelmustard on 2009-02-15
Yeah, it took me several tries to get it right.  Try every possible combination of the MPPE and such settings, eventually you should land on the right one.  It/VPNs are quite particular about this it seems.

---

### Post by bgk111 on 2009-02-15
So Im actually have trouble still.  I cant seem to get the kvpnc to work, whenever I try and run it, I get the following error message:

error: Unable to find "vpnclient" at "/usr/local/bin/vpnclient"!

Any ideas?  Im using kvpnc right now, but im more than happy to try something else.

---

### Post by k3rnelmustard on 2009-02-15
You should install the gnome network-manager, the ubuntu default.  I take it ur on kubuntu?  Anyway, I tried kubuntu on a box once, and couldn't get the VPN working without gnome-network-manager or whatever it is that's included in ubuntu.  Once I set it up there I was able to connect to it using the kde network manager though.  Anyway, I think KVPNC is for a different type of VPN connection, though I'm not sure.

---

