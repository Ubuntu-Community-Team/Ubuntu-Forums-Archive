---
title: "[SOLVED] wireless has dns resolution problem, new pci wireless card"
date: 2008-12-18
forum: General Help
---

### Post by ju2wheels on 2008-12-18
Hi everyone, I just installed a new PCI wireless G adapter (D-Link WDA-1320) into my desktop pc. I bought it as I found pretty much good reviews and read that worked out of the box with 8.04. 

Well, currently it was noticed out of the box with 8.10, however I seem to be having DNS resolution issues. For some reason, when my wireless is the active connection, DNS resolution is attempted on the DNS server that I used to use with my hardwire ethernet adapter. 

I can connect to my router over dhcp fine, I obtain an IP, however I can only visit google.com and any visit to any other domain results in a page not found due to failed DNS lookup. I only noticed it was a DNS resolution issue when I couldnt get OpenArena to find servers.

The weird part is if I use nslookup, it will use the NIC's old DNS values and fail and then attempt correctly with my wireless router as the DNS and succeed. So im not sure why for some things its working and for others its not.

I tried installing the latest madwifi since my chip is an atheros but its still a no go.

---

### Post by ju2wheels on 2008-12-20
bump, anyone.

---

### Post by ju2wheels on 2008-12-30
Just an FYI for anyone who may have a similar problem in the future:

I ended up with two PCI wireless cards, both recognized by Ubuntu 100% out of the box and both able to connect to my router over DHCP. However, initially, both were unable to resolve the domain names of any website.

I later determined the issue was in /etc/resolv.conf which was not being properly updated by the Network Manager applet when I switched adapters.

In the end I need to erase the contents of /etc/resolv.conf removing the nameservers it had for my ethernet hard wire adapter and adding the IP for my router as a nameserver.

For other more complex setups you may also need to edit /etc/networking/interfaces .

Strangely, after editing /etc/resolv.conf by hand, it now gets updated correctly on its own by Network Manager when I switch connections.
____________________________

For those wondering which wireless PCI adapters I tried which worked with Intrepid:

GIGABYTE GN-WP01GS IEEE 802.11b/g PCI Wireless Adapter - Excellent signal strength.

D-Link WDA-1320 IEEE 802.11b/g 32-bit PCI Wireless G Desktop Adapter - Works as good as the Gigabyte, but the signal strength is weaker from the same distance to the router compared to the Gigabyte.

---

