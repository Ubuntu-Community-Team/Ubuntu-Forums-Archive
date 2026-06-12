---
title: "not able to enable wireless"
date: 2010-03-25
forum: Colombia Team - Colombia
---

### Post by fevemo on 2010-03-25
Hi, 
some weeks ago my wireless stopped working and I fixed it by adding a # to [COLOR=Red]/etc/modprobe.d/blacklist-ath_pci.conf[/COLOR]

I don't know if that had something to do but today my wireless stopped working and when I restarted my computer it said that wireless was disabled and when I right click the enable wireless option is grey and I can't click it, 

when I run iwlist scan I get this:

 	Code:
 	felipe@felipe-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down 
when I run iwconfig i get this
 	Code:
 	felipe@felipe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 
[COLOR=Navy]
[COLOR=Black]does somebody know what I can do

ps: I'm have Ubuntu 9.10 and my wireless car is Atheros Communications Inc. AR5001 Wireless Network Adapter :sad:
[/COLOR][/COLOR]

---

