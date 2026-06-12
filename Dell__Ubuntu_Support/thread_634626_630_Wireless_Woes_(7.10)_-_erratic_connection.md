---
title: "630 Wireless Woes (7.10) - erratic connection"
date: 2007-12-07
forum: Dell  Ubuntu Support
---

### Post by jbbaird@hotmail.com on 2007-12-07
Ive been lucky with wireless on Ubuntu laptops - until I converted my primary one from XP.

A relatively new Lattitude 630, detecting a BCM94311MCG wlan mini-PCI card works occasionaly ... it show a cosistent and strong connection but will only resolve a name and display a page in the browser every few minutes.  Pidgin appears to work fairly consistently but most of the time I cannot access a site or ping a host.  

It does work, for short periods but something is "broke".

I do not know much about LINUX but have been running Feisty for six month ons or so without issue on another laptop (but with the ndis wrapper).

If I boot back to Windows, everything works well with the same access point but device manager reports a Dell Wireless 1390 WLAN Mini-card.  Pathetically, I'm not even sure where to look into the problem with Ubuntu - iwconfig looks fine and network manager seems to detect and report strength without issue.

Any help or suggestions appreciated!

---

### Post by MrFSL on 2007-12-07
I would suggest using wicd.

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by jbbaird@hotmail.com on 2007-12-07
Thanks!  changing the mtu size to 1492 seemed to do the trick with nm but I'll try wicd as well.

A few questions from a curious idiot ...
--how is wicd different from nm
--what must the mtu size correspond to (I picked 1492 because this value resolved a Windows VPN issue for me and I was grasping at straws)?

Thanks!

---

### Post by Monkey_Tales on 2007-12-08
You can try this **Broadcom 43xx based wireless cards the EASY way.** 			                    			 			 		 		 		
[Online (0.3.2) installer]("http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz")

---

### Post by erichill on 2007-12-08
I have been having similar problems with my Inspiron 1501.
To cut a long story short, I have added the IP address of my router to the /etc/avahi/hosts file e.g. 192.168.1.1 router.local

This seems to be working and I am reporting on it periodically in alt.os.linux.ubuntu  

You might get the same effect by adding your router address to the hosts list in your network connection, but I have not tried that yet.

Hope this helps :)

Eric

---

