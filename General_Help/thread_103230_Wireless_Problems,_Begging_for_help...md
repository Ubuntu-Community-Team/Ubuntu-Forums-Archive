---
title: "Wireless Problems, Begging for help.."
date: 2005-12-13
forum: General Help
---

### Post by Torez on 2005-12-13
Please help me. I've been having problems for weeks. I've searched everywhere but can't find a solution.

Problem is, I've set up my Ubuntu installation so that the internet comes in through eth1, a wired connection, then should broadcast on a wireless connection, Wlan0, for my PDA. The connection should be ad-hoc, for use on my RTL8180L, with no WEP key. But everytime I restart, the default gateway goes back to wlan0, forcing me to lose internet, and the wlan0 turns it's key type to hexadecimal, making the entire network name, XDA IIi shutdown. I've tried changing the name, thinking it was that, but that has had no effect. Also, when I set wireless connection key type back to Plain, my PDA then sees the wireless connection, connects, but then Ubuntu freezes, and upon restart, it's back to square one.

As long as wlan0 is actually active in the networking GUI, there's no way to set eth1 as the default gateway, meaning no internet until wlan0 is shut off. I set eth1 as default, close network GUI, internet doesn't work, and upon reloading network GUI up, it's turned itself back to wlan0.

Please help me here. I'm a complete noob at anything to do with Linux and Ubuntu. I'm learning fast, but this continually gives me problems. I honestly don't know what logs you all want to help resolve the problem, so please just tell me what to do to get the logs you need, though I will post a copy of my interfaces file, and the log of iwconfig.

Please. I'm begging you.. :( 

--- interfaces ---

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp

auto eth1

iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid default


--- iwconfig ---

admin@serverm:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100/100  Signal level:-95 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---


Note: Surprised faces in logs have invaded ": o" areas. There aren't really surprised faces in my logs or conf files, I assure you...

---

### Post by hajk on 2005-12-14
Try removing the gateway line in the wlan0 section of /etc/network/interfaces, because eth1 should be your only gateway to the internet. The connection to your PDA is a dedicated one, it does not run via the (or a) gateway.

---

### Post by nelposto on 2005-12-14
[QUOTE=Torez]I set eth1 as default, close network GUI, internet doesn't work, and upon reloading network GUI up, it's turned itself back to wlan0.[/QUOTE]

I have the exact same problem... only disabling eth0 solves it. I would be interested in hearing a solution.

---

### Post by Torez on 2005-12-14
Okay. Gateway problem solved nicely, but only more problems have appeared:

Wlan0 continually reverts itself back to "mode:auto" from ad-hoc, and the Essid turns to "ESSID:off/any", meaning my PDA doesn't see any network at all. If I type "sudo iwconfig wlan0 mode ad-hoc" and the same for ESSID, nothing happens, unless key-type in network config is set to Plain(ASCII). If I set it to plain, and have no WEP Key, the entire installation freezes up on me, and I have to restart, and the problems begin again. It will only NOT freeze if I set my WEP key to 0000 or something of the likes, but it is pretty much imperative that I have no WEP Key, as I do not know how it works or how to set it up on the Ubuntu installation and on my O2 XDAIIi ( If anyone else does know this, and thinks it will help, please feel free to show me where I can get a guide on how to do this.. ).

Gateway problem is solved though, finally, after many weeks! Thank you! But please, help me more. ;_;


---


EDIT: Forget it. I can't be bothered with this anymore. I've tried for weeks, and can't get it working. Wireless is obviously something Ubuntu doesn't like in this release. Hopefully in future releases it will work better, but nevermind, I'm not messing around with it anymore. My server is in somewhat of a high demand, and every time I play with wireless, I lose reliability, and my server config files wipe themselves.
I will continue to run my server files on Ubuntu, but it won't be forever.

Thanks for your help everyone, and to everyone suffering the same problem as me, I hope you get it solved. Heh.

---

