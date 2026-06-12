---
title: "Azureus port forwarding with 2 routers"
date: 2005-11-21
forum: Desktop Environments
---

### Post by timczer on 2005-11-21
I am having an issue with download speeds due to getting a Nat error with azureus.  I have the ports open in firestarter.  On pcflank.com the port comes up as "stealth".  My issue is that I am going through two routers.  My cable comes in , goes through its modem,  then to a broadband router for my internet phone.  This then runs to a wireless router (both are linksys).  My PC is hard wired from this router.  I have a static ip address for my PC.  My question is how do I forward the needed ports through the two routers to remove the Nat error and get better down load speeds?

---

### Post by dbott67 on 2005-11-21
You have a couple of options:

Pre-amble: to do #1, you will need to make sure that the routers are configured as separate networks.  For example, the default Linksys router uses 192.168.**[COLOR="Red"]0[/COLOR]**.xxx (I think) as the default subnet.  For your 1st router, keep these settings.  For the 2nd router, you will need to change the subnet to 192.168.**[COLOR="Red"]1[/COLOR]**.xxx (or something different, tham the first one).

1. If you want the added protection of dual NAT, you could forward Azureus ports on 1st router to the (external WAN) IP address of the 2nd router (you should set 2nd router to have static IP, if not already).

2. If you just want to have a functional network, and rely on the security of only the 1st NAT router, you could disable DHCP on the 2nd router, effectively turning the 2nd router into a simple switch.

The only caveat here is that you do not use the WAN port on the 2nd router --- only the 4 built-in LAN ports.  So, your computer would be plugged into LAN port 1 and the 'uplink' to the 1st Linksys router would be in LAN port 2, 3 or 4.  Some routers have an 'auto-sensing' capability, meaning that they can tell whether the port requires MDI (straight-through cable) or MDX (cross-over cable).  If your router does not support this, you will need to purchase/make/obtain a 'cross-over cable', otherwise, you can just use whatever patch cables you have handy.

Make sense?  If not, just ask & I will clarify.

-Dave

---

### Post by timczer on 2005-11-21
To make sure I am clear, my first router, the broadband, phone router, has an ip of 192.168.15.1, the second as an ip of 192.168.1.1.  The subnet on both is the same as 255.255.255.0.  Currently they both are set to obtain ip addresses automatically.  If I set the second router to static, it would have to be the form of 192.168.15.xxx (let's say 192.168.15.100)?  Then in forwarding on the first router I forward the azureus ports to that router address?  In the second router I would then forward the azureus ports again to the static ip of my pc (let's say 192.168.15.101)?  On my PC where I set my static ip address, does it also need to be of the form 192.168.15.xxx, and which ip address do I set as the default gateway, the first or second router?  

For option 2, would this stop the wireless connection to the internet?  I use this for my laptop around the house.

Thanks for your help.

---

### Post by dbott67 on 2005-11-21
[QUOTE=timczer]To make sure I am clear, my first router, the broadband, phone router, has an ip of 192.168.15.1, the second as an ip of 192.168.1.1.  The subnet on both is the same as 255.255.255.0.  [/quote]

Perfect.

[QUOTE=timczer]Currently they both are set to obtain ip addresses automatically.  If I set the second router to static, it would have to be the form of 192.168.15.xxx (let's say 192.168.15.100)? [/quote]

Exactly.  The external WAN IP of router #2 would be 192.168.15.100, while all of the internal addresses would be 192.168.1.xxx for devices connected to router #2.  Set your computer IP to static (i.e. 192.168.1.50).

[QUOTE=timczer]Then in forwarding on the first router I forward the azureus ports to that router address? [/quote]

Yes.  Forward them to 192.168.15.100.

[QUOTE=timczer]In the second router I would then forward the azureus ports again to the static ip of my pc (let's say 192.168.15.101)?  [/quote]

Actually, your computer would be on the 192.168.1.xxx subnet.  You could set  the IP to be 192.168.1.50 (or whatever).  Then forward Azureus ports to 192.168.1.50.

[QUOTE=timczer]On my PC where I set my static ip address, does it also need to be of the form 192.168.15.xxx, and which ip address do I set as the default gateway, the first or second router?  [/quote]

The static IP for the PC should be in the form 192.168.1.xxx (the 192.168.15.xxx is technically a different network from your computers point-of-view).  For the default gateway settings, you would use the IP of the parent router.

**_For example, the 2nd Linksys external IP, the settings would be:_**
External IP address of Router #2: 192.168.15.100
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.15.1 (IP of first router)

**_Settings for computers connected to 2nd router:_**
Static IP of computer using Azereus: 192.168.1.50
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1 (or whatever the internal IP address of Linksys router #2 is --- check the manual to be sure)

[QUOTE=timczer]For option 2, would this stop the wireless connection to the internet?  I use this for my laptop around the house.[/QUOTE]

No.  Basically, all it would do would be to pass DHCP requests to the first router.  Every device would be on the 192.168.15.xxx subnet (the 2nd router would not be functioning as a router --- only a simple 'wireless' hub/switch) 

-Dave

---

### Post by dbott67 on 2005-11-21
Here's a little diagram that hopefully will clarify. The one thing I forgot to add (on the diagram) would be that you need to setup port forwarding from router #1 to the external IP of router #2 (192.168.15.100). 

-Dave

---

### Post by timczer on 2005-11-21
Alright, got it set up the right way, I think.  I am now able to get a green light in azureus, and pcflank.com says this port is open.  I am still getting slow speed on downloads, but getting there.  Looking at the azureus wiki, it says not to use the default port of 6881 as this is often blacklisted.  I wanted to go back into my routers and change the port forwarding for azureus to a different port (with the corresponding changes in firestarter and azureus).  I can get back to config for the wireless router by typing 192.168.1.1 into my browser.  My issue is I can no longer get into my broadband router.  When I type 192.168.15.1 into the browser I get Problem loading this server error.  I was able to get into that router before I made these changes.  What am I doing wrong?

By the way, thanks for the continued help.

---

### Post by dbott67 on 2005-11-21
To connect to your IP Phone/broadband router, the IP address should be 192.168.15.1 (as you tried).  Sometimes the routers get a little confused.  Just try unplugging them & plug them back in (cycle the power).  If this fails to work, try connecting your computer or laptop directly to the broadband router (wired).  Set your IP to DHCP and then try releasing & renewing your IP address.

-Dave

---

