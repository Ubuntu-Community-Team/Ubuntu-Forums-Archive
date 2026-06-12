---
title: "Wireless Card No Longer Associating w/AP"
date: 2006-02-25
forum: Desktop Environments
---

### Post by schnarff on 2006-02-25
Hello All,

I'm running Breezy AMD64 on a machine I got over Christmas, up-to-date as of a couple days ago. I got wireless drivers loaded via ndiswrapper shortly after assembling the box, and it worked just fine with my OpenBSD access point -- until a couple of days ago, when I moved it out of the same room at the AP.

After I booted back up in the other room (which is just on the other side of the wall from the AP), I got a strong wireless signal and was on the network...until a few hours later, when the connection suddenly got super-slow and I started dropping packets, before losing the connection altogether. I suspect that this is due to another network popping up (I live in an apartment tower full of twentysomethings, so there's a good dozen wireless networks that pop on and off all the time) with a stronger signal, which is confusing my box as to which network to get on.

What's really killing me is that I can see my network if I run "iwlist wlan0 scan", I've used iwconfig to set my encryption key properly, and I've told the card (both via "iwconfig wlan0 ap 00:80:c6:e3:72:2c" and System -> Administration -> Network Devices) to use my essid. I just can't figure out why I'm no longer associating with my AP.

Since it's probably quite relevant, here's the output of "iwlist scan wlan0" (my AP is "kirknet"), "iwconfig wlan0", and the contents of /etc/network/interfaces:

> wlan0     Scan completed :
          Cell 01 - Address: 00:80:C6:E3:72:2C
                    ESSID:"kirknet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:0/100  Signal level:-42 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:46:A9:A4:E8
                    ESSID:"gumbas"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-59 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:00:00:00:00:00
                    ESSID:"kirknet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:0/100  Signal level:-46 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=11 Mb/s   Tx-Power:25 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:<my key>   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-43 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:151  Invalid misc:31266621   Missed beacon:0


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
#iface eth0 inet static
#	address 192.168.2.1
#	netmask 255.255.255.0
#	network 192.168.2.0
#	broadcast 192.168.2.255
#	gateway 192.168.2.69
#	# dns-* options are implemented by the resolvconf package, if installed
#	dns-nameservers 192.168.2.69

iface wlan0 inet static
address 192.168.1.80
netmask 255.255.255.0
gateway 192.168.1.42
wireless-essid kirknet
wireless-key s:<key string>
wireless-ap 00:80:c6:e3:72:2c

auto eth0

auto wlan0

Thanks in advance for any help you can give.

Alex Kirk

---

### Post by schnarff on 2006-02-25
Just to make things really interesting, after I posted this message, I decided to go back and try getting back on the wireless, in case I'd done something dumb. After a reboot, the box had auto-associated with an open "linksys" network, but I was able to get it to associate with my network and get back on the Internet...for about 15 minutes. Afterwards, iwconfig showed my AP as 00:00:00:00:00:00 and my essid as "Off/None". Is there some sort of messed-up process that's coming through and tweaking my wireless config based on a setting that's fouled up in /etc somewhere?

Alex Kirk

---

