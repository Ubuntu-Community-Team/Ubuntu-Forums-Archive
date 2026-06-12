---
title: "Dell Latitude C510/C610 Wireless Connectivity Problem"
date: 2010-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AndToNY on 2010-07-13
Recently I upgraded a friend's Latitude C510/C610 (Pentium III) to Ubuntu 10.0.4, after wiping the drive of Windows XP.  Seemingly everything went fine, but I cannot seem to connect to the internet wirelessly (though via ethernet works just fine).

What irritates me the most is that it does pick up wireless signals, though it cannot connect (it seemingly drops them almost as quickly as it makes them).  If feels (and keep in mind my strengths lie with the MacOS X platform; another flavor of Unix) as if things are fine&#8211;in the sense that I can at least see the other wireless signals&#8211;though the ability to connect wirelessly is crucial.

The ethernet controller is a 3Com 3c905c-TX/TX-M (rev 78) which 3Com no longer supports, so I don't see current drivers being an option.  That being said I feel so close to a solution and would hate to have to downgrade to an earlier version of Ubuntu (partially for fear of dealing with the same issue again; partially because 10.0.4 is so pretty).

Then there's going back to Windows, which I really, really want to avoid.

Any help would be appreciated.

---

### Post by jarviser on 2010-07-14
What model of wifi card is it using? You only say what ethernet card it has.

---

### Post by AndToNY on 2010-07-15
> **jarviser said:**
> What model of wifi card is it using? You only say what ethernet card it has.

Thanks for your reply (and sorry for my delay) though I am not sure that I am looking for (I mean, I know that I looking for a wi-fi card on the computer, but nothing that I am looking at actually says 'wi-fi.'

Is there something that I should be looking for?  I mean, I see stuff like "Modem Controller", PC card Cardbus Controller", "Subsystem: Intel Corporation Device 4541" and so on.

Never mind a brand of modem; what would a wi-fi card be called under these circumstances?

---

### Post by jarviser on 2010-07-16
Go to Applications - Accessories - Terminal and enter the command

lspci

and look for a line containing "Network" and "wireless" such in mine...

"0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN "

thus mine is an Intel 4965AGN

Look out for the dreaded words "Broadcom" and if it is a Broadcom card, look up the fix which appears in about 1 in 10 threads on this forum section.

It's likely that a PIII laptop of that vintage does not actually have a wifi card, but you do say it will detect signals so...

---

### Post by AndToNY on 2010-07-16
> **jarviser said:**
> Go to Applications - Accessories - Terminal and enter the command

lspci

and look for a line containing "Network" and "wireless" such in mine...

"0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN "

thus mine is an Intel 4965AGN

Look out for the dreaded words "Broadcom" and if it is a Broadcom card, look up the fix which appears in about 1 in 10 threads on this forum section.

It's likely that a PIII laptop of that vintage does not actually have a wifi card, but you do say it will detect signals so...


This is the information from Dell about the Latitude C510/C610:

System Type:    Latitude C610
Ship Date:    4/9/2002
Dell IBU:    Americas

Service Tag


Quantity    Parts #    Part Description

1    4E912    Processor,PIII,Tualatin,1G, 512K,UPGA
1    2K446    Assembly,Documentation,Cable, TSH,Cover,Latitude
1    9364U    Adapter,AC,External,20V,70W,3WBA
1    1H778    Assembly,Cable,Flex,Extended Graphics Array Liquid Crystal
Display,Data
1    1H817    Bezel,Liquid Crystal Display, Latitude,C610
1    1H821    Assembly,Palmrest,Latitude, C610
1    6P823    Assembly,Base,Notebook, OEM,Data,V2
1    71PXH    Assembly,Floppy Disk Drive, Internal/External,Notebook,
Light-WT
1    978ET    Assembly,Liquid Crystal Display with/Inverter,IBM,TFT 14.1
1    3C048    Keyboard,87,United States/ English,C600/I4K,R2
1    735HE    Mouse,PS2,6P,2 Button,Wheel 1.3A,MS,MG
1    3K238    Customer Kit,DS,CDOCK2, V.3,90W,DAO
1    9C487    Keyboard,104,6P,US,SLTEK,MG
1    0F437    Case,Carrying,Nylon,Notebook, Classic
2    864GY    Dual Inline Memory Module, 256,133M,32X64,8K,144
1    2M400    Battery,Primary,14.8V,8C, Lithium,Sanyo
1    8P495    Subassembly,Compact Disk Drive Read Write,8X,HLDS,Kit
Notebook,2
1    0E828    Modem,56K,Internal,MDC,PCTEL, GVC
1    480WV    Carrier,Hard Disk Drive, C600/I4000
1    5K804    Hard Drive,30GB,I,F2,9.5MM, Hitachi-Dogwood
1    8267R    Connector,Header,2X22,F,2, Short,Gold,35K,Third Height,CS
1    95026    System Integration,Lock, Security,Kensington
1    6797R    System Integration,Fee, Integration,#8
1    1F756    Kit,Software,Overpack,Windows 2000 Professional,SP2,F5 English


What follows below is the information from Terminal (via lspci):

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)


Nowhere listed is a device that I could see as enabling wireless; that being said, as I mentioned earlier, the computer tries to connect to wireless networks.  It fails, but the fact that it even tries seems to imply that there is a wireless card in it.

Though, following my line of reasoning, I would think that it would be listed if it were there.

Though if it's not there, why would it try to connect with wireless networks?

Stranger, and stranger.

---

### Post by jarviser on 2010-07-16
Either it's not there or it is only part detected. Does it actually list wireless networks to choose from? If so then there must be a wifi card in there but not recognised even by lspci. It must be under a cover underneath surely - though some mini pci wifi cards are under the keyboard.

I am out of my depth here.
 
Can you borrow a modern USB wifi dongle to try?

---

### Post by Tod Brubacher on 2010-09-01
I have the exact same problem, and same model laptop. so, hate resurrect a month old thread but I could really use some help. below I've pasted the terminal commands printouts. My symptom is that I see all the wifi networks around, but when I try to connect it fails instantly or continuously prompts for authentication (usr/pwd) if the network is secure. I'm at a loss, I've updated the kernel to the latest stable upstream .deb and updated the whole OS package to the latest. (it was a mini-cd install so the latest stuff came in the d-load during install) any thoughts would be wonderful:

oh and please note that this problem occurs with both the internal wireless card and a pcmcia card I have as well. the readouts below were run with both active as you can see.

[code]
csdi@thing-0:~$ lspci -nm
00:00.0 "0600" "8086" "3575" -r04 "" ""
00:01.0 "0604" "8086" "3576" -r04 "" ""
00:1d.0 "0c03" "8086" "2482" -r02 "8086" "4541"
00:1e.0 "0604" "8086" "2448" -r42 "" ""
00:1f.0 "0601" "8086" "248c" -r02 "" ""
00:1f.1 "0101" "8086" "248a" -r02 -p8a "8086" "4541"
00:1f.5 "0401" "8086" "2485" -r02 "1013" "5959"
00:1f.6 "0703" "8086" "2486" -r02 "134d" "4c21"
01:00.0 "0300" "1002" "4c59" "1028" "00e3"
02:00.0 "0200" "10b7" "9200" -r78 "1028" "00e3"
02:01.0 "0607" "104c" "ac51" "1028" "00e3"
02:01.1 "0607" "104c" "ac51" "1028" "00e3"
02:03.0 "0607" "104c" "ac50" -r01 "12a3" "ab01"[\code]

[code]
csdi@thing-0:~$ lsmod
Module                  Size  Used by
binfmt_misc             6555  1 
michael_mic             1712  8 
orinoco_cs              5082  2 
orinoco                62590  1 orinoco_cs
snd_intel8x0           26521  2 
cfg80211              149609  1 orinoco
snd_ac97_codec         99817  1 snd_intel8x0
radeon                836410  3 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75159  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4722  0 
pcmcia                 36515  1 orinoco_cs
snd_rawmidi            17635  1 snd_seq_midi
ttm                    55536  1 radeon
drm_kms_helper         30968  1 radeon
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47110  2 snd_seq_midi,snd_seq_midi_event
joydev                  9327  0 
yenta_socket           20525  0 
snd_timer              19728  2 snd_pcm,snd_seq
pcmcia_rsrc            10276  1 yenta_socket
drm                   180325  5 radeon,ttm,drm_kms_helper
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            13897  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit            4910  1 radeon
psmouse                57362  0 
snd                    49853  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7469  0 
intel_agp              25865  1 
ppdev                   5471  0 
serio_raw               4094  0 
parport_pc             27750  1 
video                  20030  0 
soundcore                880  1 snd
shpchp                 25394  0 
output                  1851  1 video
snd_page_alloc          7320  2 snd_intel8x0,snd_pcm
agpgart                32334  3 ttm,drm,intel_agp
dcdbas                  5470  0 
parport                32432  3 ppdev,lp,parport_pc
3c59x                  33860  0 
floppy                 54628  0 
mii                     4169  1 3c59x[\code]

[code]
csdi@thing-0:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:46:5f:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.0.1.9 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:01:f4:ee:63:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.36-020636rc3-generic firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: eth2
       serial: 00:02:2d:6b:f5:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.36-020636rc3-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b[\code]

[code]
csdi@thing-0:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)[\code]

---

### Post by scorpiooooooh on 2010-12-01
You said it is picking up WiFi networks... but....

Did you verify that the internal card is installed and if yes did the WiFi work with XP?

This is a strange problem but I have run into a similar issue on my own C510 with XP.  Initially, I was using a Linksys PCMCIA card (WPC54G v2.0) for WiFi  since the lappy did not come with the option installed. 

A friend of mine owns a laptop repair and resale shop, he gave me the Dell "card" to throw into the lappy.  I installed it and it was buggy as h-e double toothpicks.  I pulled it and went back to the linksys because it was faster and more reliable.  Better range and speed beats hidden and buggy.

Sometimes it's better to move on to another piece of hardware than try to make a difficult one work.  If you do have the card installed inside the lappy, I'd take it out and go with a PC Card slot solution as the first choice or a USB Network adapter.

---

### Post by dontplease on 2011-03-03
I have a c610 with the same issue, I just upgraded to 10.04. 

~# lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

I'm thinking 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) might be the wireless card

I can see wireless networks but when I try to connect with and without WEP. and it just tries for a while then kicks back the pw

edit:  was running xp and worked on this same wifi network. 
help?

---

### Post by MartijnV on 2011-03-03
Tod Brubacher seems to have a "orinoco" 802.11b card, I had one of those, got it to work with my dell c610 on Ubuntu 9 something, compiling my own driver, until the old way of communicating with the pcmcia bus became "deprecated" and the card ceased to function. Yes, the laptop sees the card on the pcmcia bus, although it seems to be a "minipci" card. An Intel 2200BG card solved these issues. (ánd 54Mbit connection!)

The list above from dontplease does'nt list a wifi card.

---

### Post by dontplease on 2011-03-05
sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:47:54:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.104 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:2c000000-2c01ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:57:b7:f4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b


maybe this helps? 
This laptop was given to me so I have never really known the specs and the dell site borderline infuriating.

---

