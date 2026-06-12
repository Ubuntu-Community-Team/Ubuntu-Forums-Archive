---
title: "Make my computer &quot;invisible&quot; on a networw"
date: 2009-04-02
forum: General Help
---

### Post by LeftNut on 2009-04-02
Hey guys,
        My goal here is to have my one of my laptops hidden on the network. I'm not really concerned if they see my ip because I know the only way to alter that is to use a proxy which is just to slow of an option for me.

My cpu specs:

Intel core duo 1.8 ghz
3Gbs of ram
2 250gb hard drives 
Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron]
Dual boot Windows Vista/Ubuntu 8.10 
(if any other information is needed just ask)


I pretty much want to hide everything but the ip address. I just want it so the other computers cant see this laptop is connected. I am the only one who can view the routers settings.


Any help would be greatly appreciated,
-Gary

---

### Post by mb_webguy on 2009-04-02
I don't think you can.  At least, I haven't been able to find a means of doing so.  Setting "browseable = no" will hide a share, but I can't find a global equivalent for hiding the server.

---

### Post by paradigm2 on 2009-04-03
Well it is very difficult.  Perhaps impossible to do if you are using a shared wireless connection.

#1 - Even if you are using WpA2-PSK with AES encryption, assuming the connection is shared that means everyone else has the passphrase.  There are programs that will sniff all the network activity and, with that passphrase, decode and show everything that you do.

Possible workarounds/minimisations:

- Use a wired connection into the router.
- use an encrypted VPN
- Make use of https, sftp, ssl, etc where possible
- Use a remote ssh tunnel

#2 - You might look into IPTABLES which is the firewall utility for linux.  It is incredibly versatile and assuming you get the configuration right, tyou can almost do anything with incoming and outgoing packets.

#3 - One Possible solution might be to run another router with all your machines on a separate subnet.  With no route from their subnet to yours, they should not be able to get to your machine.  The only things which would be in their subnet would be your router's WAN interface.  One possible solution is DD-WRT (see [http://dd-wrt.com](http://dd-wrt.com)) in repeater, or client mode.  [see docs there]

These are just a few things, there are many things to consider to accomplish such a goal.  But i bet #1 is probably the most eye opening, as well as the biggest security risk.

---

