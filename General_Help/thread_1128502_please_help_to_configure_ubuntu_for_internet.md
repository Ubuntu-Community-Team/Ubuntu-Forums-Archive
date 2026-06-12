---
title: "please help to configure ubuntu for internet"
date: 2009-04-17
forum: General Help
---

### Post by akib on 2009-04-17
i have installed ubuntu  8.04 besides windows xp sp2. i've broadband internet connection. My ISP has given me an ip address, subnet mask, default gateway, prefered DNS, alternet DNS, and also a  network address (MAC). I have no problem browsing internet with xp. But, no way i'm able to connect to internet in ubuntu. How can i change the mac address  and put the other information in the appropriate places? can anyone help me? please.........

---

### Post by doas777 on 2009-04-17
your ISP gave you a MAC?
I've never heard of them doing that before. usually your MAC is embedded on a rom on your network card. you can change it in driver software, but, there is always a risk that it will conflict with a neighbor. 

this tutorial covers the macchanger script for altering your mac address
[http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html](http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html)

try resetting your cable modem ( unplug it for 45sec to a minute). bring the cablemodem up, and then boot ubuntu.
does it work now?

---

### Post by mb_webguy on 2009-04-17
The information needs to be entered in System->Preferences->Network Configuration.  Click the tab for the type of network (i.e. Wired, Wireless, Mobile Broadband, etc.).  Click the Add button to add a new network configuration.  Give it a name if you want, such as "Home" or "Default".  While, as doas777 mentioned, it's odd that they gave you a MAC address, you can add the MAC address in the Wired tab.  On the IPv4 Settings tab, change the Method to Manual.  Click the Add button and enter the IP Address, subnet mask, and Gateway.  Add the DNS server addresses in the DNS Sever box.  Once you're done, click OK.

---

