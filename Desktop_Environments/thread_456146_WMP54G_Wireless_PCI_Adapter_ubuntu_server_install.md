---
title: "WMP54G Wireless PCI Adapter ubuntu server install"
date: 2007-05-27
forum: Desktop Environments
---

### Post by Anandsun on 2007-05-27
INSTALL ndiswrapper
sudo apt-get install ndiswrapper-utils

update will pause at 99% please be patient and let it complete
sudo apt-get update

Copy the Windows drivers for the card into a convenient directory.
They will include Rt61.INF and Rt61.sys and Rt61.cat files.
ndiswrapper -i Rt61.INF

To see them listed. One will have both driver AND hardware listed.
ndiswrapper -l

To see your wireless card listed. It won't be secured and will probably have 'any'as the essid.
iwlist ra0 scan

To set your wireless card up.
iwconfig ra0 essid youressid enc yourhexkey

Disable security on the wireless router. verify you are connected through the wireless router
ifup ra0


disconnect the wired ethernet cable and disable the interface
ifdown eth0


To see if it will mount.
ifconfig

If your wireless router issued you an IP address it will be listed by ifconfig. Make sure it didn't bind to your eth0 card instead.
If you are connected then issue
ndiswrapper -m


browse the internet.

---

### Post by ariel on 2007-05-27
I wanted to share my experience with this card. I was not so lucky, maybe my hardware version ((WMP54G v4.0) is different from yours. Anyways, here it goes.

I've been fighting with this card for about 2 years now in linux/ubuntu. The native linux drivers (serialmonkey project) never worked properly for me (I tried all their releases including various next-gen rt2x00); they work OK for a few minutes or hours, then I started getting getting weird latencies (2 to 4 seconds between my PC and my linksys router, if you can believe it) and packet loss, and the connection became unusable. This happened with WEP, WPA, and with no encryption. Note that under WinXP, I could leave the machine connected for weeks with no problem.

In Breezy/Dapper/Edgy, ndiswrapper mitigated this problem only when using a very old ndiswrapper 1.22; using any other version would again produce the weird latency problem. With Feisty, I could find no ndiswrapper version that worked reliable for more than 24h. Also, there are many known problems with NetworkManager and ralink cards, which had forced me to remove NM.

So I got sick of the Ralink chipsets and their poor linux support. Two weeks ago I bought a  Netgear WG311T, because it comes with the Atheros chipset. I had heard good things about the madwifi project that has been supporting native linux drivers for atheros for many years now.

I couldn't be more happy with my WG311T. It worked out of the box. Supported by NM and all. Solid and reliable, same performance as the wmp54g when the latter dared to work. 

And very cheap. I bought a refurbished WG311T in ebay for about the third of what I had paid for the freaking wmp54g.

---

