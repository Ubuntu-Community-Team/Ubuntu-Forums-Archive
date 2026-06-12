---
title: "Wireless Connection Shows Connected by No Internet"
date: 2009-04-08
forum: General Help
---

### Post by OmaSteak on 2009-04-08
Hello,
Absolute newbie here.  Running Ubuntu 8.14 on a Dell mininote.  I can connect to my home wireless network (2Wire router) and successfully ping the router.  The little network display icon changes from "searching swirl" to set of bars.  However, I have no active internet connection when I open the web browser to view a website.  The router uses a ten digit number as a key for the WEP security and the network connection function seems to have accepted the key, hence the connection to the router seems active.  Any suggestions to get my highspeed cable access working over the wireless network would be greatly appreciated.  BTW, it connects perfectly via ethernet cable with internet enabled without any input from me in set up. 
OmaSteak

---

### Post by PreviousN on 2009-04-08
Hmmm. So, if you plug directly in via ethernet it works, but if you connect via wifi it doesn't? 

Interesting. Can you successfully connect to another wifi public network and see if it works? There are two vectors for problems here: either your laptop's wifi isn't working, or your wireless router isn't working properly. If you can connect your laptop successfully to another wifi accesspoint, and browse the net, then the problem lies with your router. If not, we may have to troubleshoot your laptops wireless. Chances are, however, if you can "see" and connect to the network, the problem may not be ubuntu. 

BTW: if you're just using WEP encryption on your wireless router, any twobithack could break the encryption and steal your internet connection in about 5-10 minutes. I would suggest changing to WPA encryption immediatly.

---

### Post by PreviousN on 2009-04-08
Deleted accidental doublepost.

---

### Post by OmaSteak on 2009-04-09
> **PreviousN said:**
> Hmmm. So, if you plug directly in via ethernet it works, but if you connect via wifi it doesn't? 

Interesting. Can you successfully connect to another wifi public network and see if it works? There are two vectors for problems here: either your laptop's wifi isn't working, or your wireless router isn't working properly. If you can connect your laptop successfully to another wifi accesspoint, and browse the net, then the problem lies with your router. If not, we may have to troubleshoot your laptops wireless. Chances are, however, if you can "see" and connect to the network, the problem may not be ubuntu. 

BTW: if you're just using WEP encryption on your wireless router, any twobithack could break the encryption and steal your internet connection in about 5-10 minutes. I would suggest changing to WPA encryption immediatly.
Hello and thanks for the quick response.  There isn't a problem with my wireless router (2Wire).  It works with wireless notebooks running XP without a hitch.  I know the WEP security feature is out of date but it's an old router and doesn't support WPA security.  There has to be some setting in Ubuntu that I've missed that would allow/enable internet access with a wireless connection showing it is established (successful router ping).  Do I need to enter DNS info someplace in the settings for wireless function or is that automatically assigned via the router settings?  I didn't have to specify anything when I booted up with ethernet cable attached.  It was recognized on the wired network and had internet access.  If I can't get the wireless functioning fairly easily, I'm going to convert the 901 to XP and forget Linux.  I don't like that option but I don't have the time to spend messing around.  BTW, I got this Dell as a gift not expecting it to be Ubuntu.  Thanks!

---

