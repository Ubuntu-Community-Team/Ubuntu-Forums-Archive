---
title: "HELP! Lost all internet connections ubuntu eee"
date: 2009-05-29
forum: General Help
---

### Post by sirtah on 2009-05-29
Hello, 

I´m a linux rookie. I have a eee that I run ubuntu on and I started it today and I lost my wireless internet connection. I never was able to get the wired connection to work so I feel lost and hopeless. All my normal wireless tricks are not working. I need help. The only thing that I can think would have messed something up is that I ran the computer janitor last time I used my eee. I have no idea what was removed nor can I figure out how to find out.  Now when I click on the network monitor applet it simply says: 

Please contact you system admin ... to resolve the following problem: 

SIOCGIFFLAGS error: No such device 

------

ifconfig returns 

lo Link encap:Local Loopback ... 

iwconfig returns 

lo no wireless extensions 
eth0 no wireless extensions 
pan0 no wireless extensions 

nm-tool (what I used to use to find wireless connections) returns 

-Device:eth0 ----- 
 blah blah blah (nothing about wireless)

lspci returns (among other things) 

01:00.0 Network controller: RaLink RT2860
03:00.0 Ethernet controller: Attansic Technology Corp ... (rev b0)

Network tools shows for devices 

lo 
eth0
pan0 (I´ve never seen pan0 before it´s always been ra0)

in /etc/modules I have listed
lo 
rt2860

in /etc/network/interfaces I have listed 

auto lo
iface lo inet loopback 

auto eth0
iface eth0 inet static 
blah 
blah 

In the history of the synaptic package manager the last change was 

ntpdate(1:4.2.4p4+dfsg-7ubuntu5) to 1:4.2.4p4+dfsg-7ubuntu5.1

I have my computer configured for a trip I´m about to take (kde installs, spanish dictionary, spanish language setup, etc) and I do not want to reinstall and start from scratch. Please help!

Thank you in advance.

---

