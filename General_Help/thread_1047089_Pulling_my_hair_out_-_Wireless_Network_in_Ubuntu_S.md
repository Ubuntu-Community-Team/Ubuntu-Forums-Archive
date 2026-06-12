---
title: "Pulling my hair out - Wireless Network in Ubuntu Studio 8.10"
date: 2009-01-22
forum: General Help
---

### Post by floatingpoint on 2009-01-22
I have searched high and low, and I can't find a solution for this.

I have a Belkin USB wirless adapter that works out of the box in regular old Ubuntu. However, in Ubuntu studio, I can't even get the Network Manager to appear. It's as if it wasn't included in the package.

I found this: [http://robwicks.blogspot.com/2008/12/ubuntu-studio-missing-network-manager.html](http://robwicks.blogspot.com/2008/12/ubuntu-studio-missing-network-manager.html)

He says, 

> I recently install Ubuntu Studio 8.10 64 bit on a Dell Latitude D630. The wireless would not work, even after installing the restricted drives. The Network Manager icon did not appear in the gnome panel. After a bit of Googling, I found that ¨nm-applet" might not appear if the /etc/network/interfaces file has definitions for anything other than the lo interface. So, edit that file and remove the stanzas which refer to eth0, eth1, wlan0, ath0, etc. Now I see the normal network manager icon in the panel.

When I type "gksudo gedit /etc/network/interfaces" it says:

```
#This file describes the network interfaces available on your system
#and how to activate them. For more information, see interfaces(5).

#The loopback network interface
auto lo
iface lo inet loopback
```

This seems to be a major oversight with UbuStu but surely a lot of people have it working or there would be more discussion.

Can anyone help?

P.S. Even if anyone has some general knowledge on connecting to a wireless network, or a wired network (if I could do that, I could try to download Network Manager), please don't hesitate to offer advice!

---

### Post by Bao2 on 2009-01-22
Download Network Manager. There are too in Sourceforge a Network Manager specialized for wireless but I don't remember now the name. With the Network Manager I think you will not have problems.

---

### Post by cfc1960 on 2009-01-22
I agree with you. I installed Ubuntu Studio yesterday. Network Manager is not included in the software, which seems a major oversight. I have not been able to configure a network connection yet. Using a terminal I find my wireless NIC card is disabled. Interestingly I have Puppy Linux installed as well as Win XP and they are both connected normally.

---

