---
title: "bitorrent (transmission) problems"
date: 2009-05-11
forum: General Help
---

### Post by tjh196 on 2009-05-11
i have just switched over to ubuntu 9.04 from xp and i am new to this.  i am trying to use transmission to download torrents but in the preferences window it says that port 51413 is closed.  i had this problem with bitorrent in windows and had to change to a static ip instead of dynamic.  do i need to do this in ubuntu and if so how do i do it. btw i have firestarter firewall installed but the port is closed with it on or off.  i have a netgear wgr614 v7 wireless router also.  limewire works fine though.  any help would be appreciated.

---

### Post by mb_webguy on 2009-05-11
First of all, in relation to Firestarter...  You probably don't need it, and in my experience firewalls on Linux desktops cause lots of headaches yet don't necessarily make your system more secure.  You might want to check the links in my signature about security for more information.  Also, Firestarter isn't actually your firewall.  Firestarter is a GUI configuration utility for iptables.  Depending on what you mean by Firestarter being "on" or "off", you may not actually be doing anything.  Firestarter is used to change iptables settings, and iptables is always "on".  Unless by "off" you're talking about changing the settings to not block any ports, this could still be the problem.

Second, if you're using a router, then you would have to set up [port forwarding]("http://www.pcwintech.com/port-forwarding-netgear-wgr614-v7-netgear-firmware") on the router.  (Also, if you're using a router, a firewall is doubly unnecessary.)  You *will* need to set a static IP for your computer in order to do this.  Go to System > Preferences > Network Connections.  Select the tab for your connection type, select your connection from the list, and click Edit.  On the IPv4 Settings tab, change the Method to Manual.  Enter your desired static IP for the Address.  The first three numbers should be the same as the router's IP, and the fourth number should be pretty much anything you want, within some limits.  I'd suggest something between 10 and 50.  Now enter 255.255.255.0 for the Netmask, and your router's IP for the Gateway and DNS Servers.

Now you can use that static IP to set up port forwarding for Transmission.

---

### Post by chirojoseph on 2011-01-24
thanx so much mr webguy for this little paragraph youwrote way back when about port forwarding and static IP addresses...finally got my TOrrenting back again ...first time with Linux after years of XP


just wanted youto know your help was much appreciated...even 3 years down teh line! jeje..

gracias!
josefo

---

