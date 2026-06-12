---
title: "wlan not starting on boot"
date: 2005-12-29
forum: General Help
---

### Post by Stokes on 2005-12-29
hi everyone,

I think I read all the articles and wikis about that topic but found nothing to help me, or overlooked it. hopefully someone out there can and will help me.

my wireless works fine, when I configure it manually. what I want is to start wlan on boot. when ubuntu boots, it hangs a few moments at "configuring network interfaces" and the led for my wlan flashes a few times, but then it continues and no wlan connection is established.

now the interesting part is that i can say "sudo ifdown ath0" (ath0 is the name of my wireless card) and afterwards "sudo ifup ath0" and everything works fine. this confuses me completely because I suppose that nothing else happens at boot time (and I also assume that this indicates that all drivers and config-files are set up correctly).

all output (as can be found below) is almost the same after boot and after configuring the interface. even the wep-key is printed correctly in 'iwconfig'. i do not have an ip and i do not have a connection to the access point. module is loaded, essid and key is set.

i tried to rearrange the lines in /etc/network/interfaces but nothing helped. i deactivated wep-authentification for testing, but that seemed not to be the problem. 

any ideas?

thx and greetings
stokes

---
system information:
ibm thinkpad t43p
wlan: IBM 11a/b/g Wireless LAN Mini PCI Adapter II ( [link from thinkwiki]("http://www.thinkwiki.org/wiki/IBM_11a/b/g_Wireless_LAN_Mini_PCI_Adapter_II") )
ubuntu 5.10 with kernel 2.6.12-10-686 with restricted modules (madwifi is installed and loaded)

--
output of  lshw -C network

*-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@04:02.0
       logical name: ath0
       version: 01
       serial: 00:14:a4:30:44:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.1.38 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:a8400000-a840ffff irq:21

---
output of lspci -v

0000:04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: IBM: Unknown device 057e
        Flags: bus master, fast Back2Back, medium devsel, latency 168, IRQ 21
        Memory at a8400000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

---
output of lsmod | grep ath
ath_pci                78908  0
ath_rate_sample        17000  1 ath_pci
wlan                  141692  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample

---
output of iwconfig ath0

ath0      IEEE 802.11g  ESSID:"***"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:C5:62:B9:33
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:***  Security mode:restricted
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:6  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---
output of ifconfig ath0
ath0      Protokoll:Ethernet  Hardware Adresse 00:14:A4:30:44:3B
          inet Adresse:192.168.1.38  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::214:a4ff:fe30:443b/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3391 errors:3 dropped:0 overruns:0 frame:3
          TX packets:4427 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:200
          RX bytes:2810099 (2.6 MiB)  TX bytes:548138 (535.2 KiB)
          Interrupt:21 Speicher:f8ba0000-f8bb0000

---
content of /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0

iface ath0 inet dhcp
wireless-key s:***
wireless-channel 6
wireless-essid ***

auto ath0

---

### Post by Juergen on 2005-12-29
Maybe it's the german messages ;-)
You know there's a very active community at [http://www.ubuntuusers.de](http://www.ubuntuusers.de) ?

You say the messages are 'nearly' identical... maybe a diff would help?

---

### Post by Stokes on 2005-12-30
i found another difference.

if the card does not work,  iwconfig gives:
ath0      IEEE 802.11  ESSID:"***"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:***   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

if it works:
ath0      IEEE 802.11g  ESSID:"***"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:C5:62:B9:33
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:***   Security mode:restricted
          Power Management:off
          Link Quality=47/94  Signal level=-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

see the small "g" after IEEE 802.11 ? does that mean something?

greetings stokes

---

### Post by Stokes on 2005-12-30
the complete diff of the informations i have. 
nothing that surprising, except that little "g". 
any ideas?

greetings stokes

 diff not_lshw work_lshw
28c28
<        configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
---
>        configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.1.33 multicast=yes wireless=IEEE 802.11g

no differences between not_lspci and work_lspci
no differences between not_lsmod and work_lsmod


diff not_iwconfig work_iwconfig
1,3c1,3
< ath0      IEEE 802.11  ESSID:"***"
<           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00 
<           Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
---
> ath0      IEEE 802.11g  ESSID:"***"
>           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:C5:62:B9:33 
>           Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
7c7
<           Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
---
>           Link Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm


diff not_ifconfig work_ifconfig
1a2
>           inet Adresse:192.168.1.33  Bcast:192.168.1.255  Maske:255.255.255.0
4,5c5,6
<           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:7 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
7c8
<           RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
---
>           RX bytes:998 (998.0 b)  TX bytes:1236 (1.2 KiB)

---

### Post by Stokes on 2005-12-30
finally found a way to get my wlan working. did not solve the problem but it now works.

added a line to /etc/network/interfaces:

pre-up /sbin/iwconfig ath0 key restricted s:*** essid ***

now the interface gets configured twice, this seems to do the trick.

thx and happy new year.
stokes

---

