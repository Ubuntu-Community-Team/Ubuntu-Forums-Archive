---
title: "WI-FI drivers for Dell Latitude D600"
date: 2011-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Green_msk on 2011-01-06
Hi all. Please help me to bring up wi-fi interface on Dell D600 laptop. Chipset - Broadcom 4306 (aka Dell wireless 1350).  From the BIOS side it`s enabled. 

There is a full (pure) OS installation. Ubuntu versions 9.04 (desktop and Dell OEM), 9.10 and 10.10 (desktop and netbook) were used - no significant differences. Now I`m talking about ver. 9.10

lspci
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

lspci -n
02:03.0 0280: 14e4:4320 (rev 03)

Wiki, Google and forums were used - there are 3 common solution found:

1) Proprietary driver b43 activation. I did it just after OS installation through Prop. driver manager and manually by b43-fwcutter installation from the terminal as well. I can see wlan0 in ifconfig (iwconfig) output but Wireless tab still empty in Network Connections utility. 

2) Use the Win driver with ndiswrapper. I did it with old driver (R102320) which was working fine on this machine under XP and latest one (R115321) downloaded from Dell website. All alternative drivers were disabled and added into blacklist.conf beforehand as required. Now it look like this:

ifconfig
  wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:9f:08:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 &#1055;&#1072;&#1084;&#1103;&#1090;&#1100;:fafee000-faff0000 

iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

WLAN folder still empty. The command "ifconfig wlan0 up" has no affect.

3) Use STA driver. The only one I could obtain was  hybrid-postsrc_x86_32-v5_100_82_38.tar.gz 
Installation went without errors, but wlan0 interface doesn`t seen at all in ifconfig output.

Please help me to solve this problem. I`m not thoroughly familiar with Linux, so step-by-step instructions is preferred for me.

Thanks in advance!

---

### Post by mikewhatever on 2011-01-07
Do you see any networks when clicking the Network Manager applet in the panel? The 'Wireless tab in the Network Connections utility is supposed to be empty, unless you have any configured networks.

I remember using b43 with Karmic to run the bcm4312 card, and it didn't work without the linux-backports-modules-wireless-karmic-generic package installed. On the other hand, that same package had to be removed when using STA.

---

### Post by Green_msk on 2011-01-07
Yes you`re right. After I`ve configured manually one of networks the  keyring was just created and after reboot I can connect to the  configured AP and can see/connect to all other APs around me.

Thanks a lot.

PS: Finally wifi is working under proprietary b43 driver without any additional packages.

---

