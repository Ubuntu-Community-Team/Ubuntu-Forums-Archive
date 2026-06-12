---
title: "customized 1525"
date: 2008-09-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ItalOz on 2008-09-08
I am in the process of buying a 1525 myself, unfortunately here in Italy they do not give you the option to have it shipped with Ubuntu.
So my plan is to buy it and install Ubuntu afterwards.
Dell Italia does not give you even advices on hardware compatibility.

Thus I ask you if any has tried an inspiron with the following customization:

- Display TFT widescreen WSXGA+ (1680 x 1050) 15,4" with TrueLife™

- Processor Intel® Core™ 2 Duo T8100 (2,10 GHz,FSB 800 MHz, cache L2 3 MB)

- Mini card Wireless-N Intel® last generation, Europa - Core 2 Duo Processors

Particularly the last item worries me most, since I red that the Dell card does not work fine with Ubuntu I changed for this one, is it the right one?

And about 1st item, any of you has tried that resolution screen?

Thanks in advance, be fine

---

### Post by wgarider on 2008-09-09
*I red that the Dell card does not work fine with Ubuntu *

I could be wrong but I have the Dell wireless card and it's actually a Broadcom. I made it work with 8.04.1.... you know that you can download a Dell build of 8.04.1 as an ISO that is for the 1525?

Here's a link: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by ItalOz on 2008-09-09
thanks for the reply, the options I am given on the website for the wireless card are:

1) mini Dell™ Wireless 1395 802.11b/g - Europa

2) mini Dell™ Wireless 1490 802.11a/b/g, Europa - Core 2 Duo Processors

3) mini Wireless-N Dell™ Wireless 1505, Europa - Core 2 Duo Processors

4) Mini Wireless-N Intel® (last generation) Europa - Core 2 Duo Processors

so I have to choose one out of these four.
Since I red that some people had trouble with the Dell wireless cards and less with the Intel I though getting option 4) but the specs (last generation) are pretty poor.

So does any of you have tried any of the wireless cards listed here with Ubuntu.

Thanks for the link to the Ubuntu ISO

CIAO

---

### Post by wgarider on 2008-09-10
ItalOz, sorry for the delay.....

Here's what I have, per the Dell website. I ran my service tag andd got the list of hardware as the factory built it. It lists my wirless card as: part# **JR356**	descr: **CRD,WRLES,MCRD,DW1395,4312BG**

That's consistent with what I see from Ubuntu when I run:
[B]remote:~$ lspci | grep Broadcom
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/B]

I know this combination of hardware and Ubuntu 8.04.1 will work with the Dell Wireless 1395 .......hope this helps.

---

### Post by cole24x on 2008-09-10
i just installed ubuntu 8.04 on my 1525 laptop everything works. make sure you do updates with hardwire internet before you do anything thats how i got my wireless to work.

---

### Post by ItalOz on 2008-09-21
well I could not read the forum for a while.
But in the meantime today arrived my new inspiron 1525.
It came preloaded with Vista.
I am in the process now of moving the partitions to make some room for the Ubuntu installation. It's gonna take 3 more hours to finish moving, resizing, formatting. (5 overall)
Thus unfortunately I will not be able to install Ubuntu till tomorrow.
I am very curious to see how everything will work.

I'll install Ubuntu from the normal distribution and not from the Dell ISO  image because I want to have dual boot with default Vista (which anyway I paid for and now it is mine! :-x ).
Then I'll try to add all functionalities bit by bit [-o<

I'll keep updated and cry for help if needed :-)

---

### Post by wgarider on 2008-09-21
Good luck - you'll enjoy 8.04 !

---

### Post by ItalOz on 2008-09-28
well I did it. I had a long weekend and I could install ubuntu 8.04 on my new computer.
First I have to say that I did not care about dell direct or these things, I just wanted to check if ubuntu was working and actually it does.
So I made some space on the disk and I installed ubuntu.
Screen resolution was ok 1680x1050 from the beginning.

Then I wired it to the network and downloaded updates. 
Wireless started working since then.

I have to put the name of my wireless lan manually because it does not seem to have a function like "browse the nets you see around" or at least I don't know how to do it. But I know the name of my net since I set it up and the PC finds and connects to it.

For the blue wireless light to be on I followed this procedure 
```

sudo apt-get install linux-backports-modules-hardy
sudo modprobe -r iwl4965
sudo modprobe iwl4965
```

I found out the numbers by issuing ```
hwinfo --wlan
```

and answer was
```

06: PCI b00.0: 0282 WLAN controller                             
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_4229
  Unique ID: y9sn.ed0bYDPGzY8
  Parent ID: qTvu.TkjeLK60Af8
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:0b:00.0
  SysFS BusID: 0000:0b:00.0
  Hardware Class: network
  Model: "Intel WLAN controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4229 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1121 
  Revision: 0x61
  Driver: "iwl4965"
  Driver Modules: "iwl4965"
  Device File: wlan0
  Device Files: wlan0, wmaster0
  Features: WLAN
  Memory Range: 0xfe7fe000-0xfe7fffff (rw,non-prefetchable)
  IRQ: 506 (no events)
  HW Address: 00:21:5c:5a:23:ed
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 36 40 44 48 52 56 60 64 100 104 108 112 116 120 124 128 132 136 140
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 5.18 5.2 5.22 5.24 5.26 5.28 5.3 5.32 5.5 5.52 5.54 5.56 5.58 5.6 5.62 5.64 5.66 5.68 5.7
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00004229sv00008086sd00001121bc02sc80i00"
  Driver Info #0:
    Driver Status: iwl4965 is active
    Driver Activation Cmd: "modprobe iwl4965"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

```

worked fine

So now I am happily playing around with it.

One thing I could not solve yet is the "block number" function, in windows works in ubuntu does not (but the light show up). Any clue will be appreciated.

I'll keep you updated

Ital-Oz

---

### Post by ItalOz on 2008-09-28
also webcam now works, out of the box, siply had to install and launch cheese

```
sudo apt-get install cheese
```

and the run it!

cool, I like this Dell till now ;-)

---

