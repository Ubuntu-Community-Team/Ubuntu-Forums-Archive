---
title: "Unresponsive menu items in network manager applet"
date: 2011-02-01
forum: Desktop Environments
---

### Post by theburningor on 2011-02-01
I've noticed an issue since the last 10.10 update with the network manager applet.  When I first start gnome, the network manager works fine.  However after some length of time or trigger that I don't fully understand yet, it ceases to function any more.  None of the menu items respond.  The issue does not seem to be with the actual networking system as I can connect to the internet, ssh, etc fine.  I can restart the applet like so:

```
killall nm-applet

/etc/init.d/NetworkManager restart

nm-applet
```

But it will eventually return.  Is anyone else having this issue?

I am running 10.10 on an Asus ul30a with Gnome

---

### Post by Havel on 2011-02-01
I have the same problem on 3 computers. Haven't found a solution. Will keep you informed if I find something.

---

### Post by Havel on 2011-02-03
Bump...nobody having the same problem?

---

### Post by theburningor on 2011-02-08
There's a [thread over in Networking and Wireless]("http://ubuntuforums.org/showthread.php?t=1671574&highlight=nm-applet") that mentions a similar issue with nm-applet taking up a huge amount of RAM and reverting to non-themed icons.  I'll check on my RAM usage for nm-applet next time that it crashes to see if I'm having the same thing happening.  I don't have the icon issues that are mentioned in that thread, but when I'm on VPN, the Wireless signal strength is gone and I just see a lock icon with a blank space for the signal strength. (See attachment)

---

### Post by theburningor on 2011-02-09
It's difficult for me to gauge this, but it seems that this problem is primarily affecting me when I'm on VPN.  I am on VPN most of the day and VPN seems to drop out when nm-applet crashes so that's when I generally notice the issue, but I've had several weekends/evenings where I was not on VPN at all and have not noticed any issues with nm-applet crashing. I'm using the openvpn plugin for nm-applet to connect to my vpn and I should mention that the openvpn command-line client seems to work fine.  It seems mostly to be related to the openvpn nm-applet plugin.

---

### Post by Havel on 2011-02-09
I also using openVPN. So it is most probably related. But the problem occurs even when I dont use a open vpn connection.

---

### Post by theburningor on 2011-02-11
Alright. I found the [Launchpad bug thread]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/684599") on this and think I have it figured out. 

Certain sources (notably Elementary Desktop's PPA) have a version of network-manager-gnome which is newer than the one in the canonical maverick repository.  A fix has been issued for Natty, but is not in the Maverick repos yet.  So Ubuntu sees the newer version in elementary-desktop, uses that instead of the canonical one and, hence, the bug.  

The solution is to roll back the version of network-manager-gnome to the 0.8.1+git.20100809t190028.290dc70-0ubuntu3 from 0.8.2+git.20101123t161608.f143e76-0ubuntu1

This can be done from synaptic by searching for network-manager-gnome and then clicking 'force version' in the package menu.

---

### Post by Havel on 2011-02-11
Wow this is great. Have you tried it. Will try it when I get back home tonite. Thank you.

---

### Post by theburningor on 2011-02-11
Yeah. I've been enjoying a steady 7.1 mb of usage with openvpn on.  Everything looks good.

---

### Post by Havel on 2011-02-11
Well, this is what this community is about. I'm always impressed. Thanks man! It works. I guess we have to be carefull with updates.

---

### Post by theburningor on 2011-02-12
Yeah. I have a bad habit of adding ppa's for just about everything I'm interested in and then a) cluttering up my repository index and b) forgetting that I've even installed it. Did a massive cleanup of my ppa's after this.

---

### Post by Visitor.Q on 2011-02-22
I also had this problem. I did not really expect the network-manager applet to be in this PPA anyway. Well, I removed the PPA entirely and installed the original network-manager-gnome. Hopefully back to normal :)

---

