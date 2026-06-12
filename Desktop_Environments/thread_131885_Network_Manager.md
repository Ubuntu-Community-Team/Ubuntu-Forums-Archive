---
title: "Network Manager"
date: 2006-02-17
forum: Desktop Environments
---

### Post by rbrugman on 2006-02-17
I'm looking for some advice.  The one reason that I'm not using linux full time is because of networking. At home I have encrypted wireless, at school I have unencrypted wireless and at work I have to plug in.  When I boot Ubuntu, it sits at the network interfaces portion for a good five minutes before finally finishing.  I installed network-manager, which works decently, but I'm wondering if there is an easier way.

Can anyone offer any suggestions on how to get my networking problems taken care of?

Also, is there a way to get sound level bars to appear on the screen when I press the volume up and down buttons on my Thinkpad?


Thanks for helping!
Robert

---

### Post by hajk on 2006-02-17
The network-manager package (with the nm-applet) is about as easy as it gets in Linux, the alternative being to take out (or comment out) all the "auto" lines (except for the "lo" interface) and "map" lines for the interfaces in /etc/network/interfaces. You can then manually activate/deactivate the interfaces that are available in System/Administration/Networking, including choosing the particular wireless network and settings with "Properties".

About the volume bars for your ThinkPad: install the "tpb" package from the universe or multiverse repository (I forgot which).

---

### Post by vayde on 2006-02-18
You can also change the timeout in /etc/dhcp3/dhclient.conf.

First you will have to uncomment the line, and then change the default of 60 seconds down to something more reasonable.  Personally I use 10.

You might have to expirament with the settings a little bit.  Some DHCP servers are slower than others, and too short of a timeout might prevent you from getting an IP.

---

