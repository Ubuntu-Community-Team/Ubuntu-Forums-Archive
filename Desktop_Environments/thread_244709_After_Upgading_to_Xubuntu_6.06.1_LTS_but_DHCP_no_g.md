---
title: "After Upgading to Xubuntu 6.06.1 LTS but DHCP no go"
date: 2006-08-26
forum: Desktop Environments
---

### Post by frankhs on 2006-08-26
After I re-imaged my Dell Inspiron 3200 laptop to Xubuntu 6.06.1 LTS the DHCP doesn't work.  The Dell is an "antique" Pentium, II laptop with a maxed out RAM of 144 megs.

Previously I'd run Xubuntu 6.06 BETA with a Hawking HWC54G WiFi card (Prism GT Softmac) using NDISwrapper and the updated Rev T driver from the Hawking website and all was kool. For ease of connection I used WiFi-Radar. Everything ran well. I'd updated via Synaptic all availiable upgrades as the two months I'd ran it went by with no problems.

My WiFi card will connect and Samba with my home system just fine. Quick connections to the static IP and no problems using the LinNeighborhood program to mount shares. Full 54 MB/Sec data rates and all. Iwconfig shows "wlan0" working fine and ifconfig shows the TCPIP is set up right. 

The DHCP just doesn't get an address. It requests one and then fails after trying awhile. Using dhclient in the therminal it requested an address but DHCPDISCOVER tries but failes to get an address. 

Tried disabling the ipv6 in in the "alieses" file as I'd seen recommended in a Ubuntu WiFi troubleshooting page but: no joy.

Any ideas? Of should I just go but a directly supported card? Any idea why only the DHCP *only* doesn't work when everything else seems happy?

Thanx

Frank Harris-Smith

P.S Xubuntu and Ubuntu and Kubuntu *and*Eubuntu are in my Not So Humble Opinion as good as Linux gets...

---

### Post by Doogys on 2006-09-05
Hi Frank, 

I had the same issue with Drapper. 
After getting trouble to get my card able to scan, Then i could connect but no way to get an IP from my router (DHCPDISCOVER issue). 

It was no problem to connect to another router in my area, but not my Linksys WAG54G ;-(

Today troubleshooting for an install of sendmail (boot failure)

I discovered That in the following directory: etc/network/if-down.d/ 
I had a script called "wpasupplicant" i am not using WPA for my router. 

Then I deleted the script (to avoid to run when setting up my Network)

Miracle... It works now. 

Hope for you that it will fix your issue. 

Best Regards, 
Julien

---

