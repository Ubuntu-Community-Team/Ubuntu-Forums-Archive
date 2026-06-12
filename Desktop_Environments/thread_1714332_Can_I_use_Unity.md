---
title: "Can I use Unity?"
date: 2011-03-25
forum: Desktop Environments
---

### Post by LewisGNoa on 2011-03-25
[FONT=Arial Narrow][SIZE=2]All right, i do not now how to find out what my specs are. I do now online that it has a 
**2.133 GHZ[B] Anthlon, and 256 MB RAM. I **can't find out the Graphis Card, and this[ site]("http://www.amazon.com/HP-Pavilion-ze4805us-Laptop-Athlon/dp/B0002FBN40")[/B] says i have only  60 GB HD, BUT IT REALLy has[/SIZE][/FONT] 230 some odd amounts of GB. So can it use Unity (HP Pavilion ze4805us) O yeah, its "designed" for XP

---

### Post by ShakeyJake on 2011-03-25
System>Preferences>Hardware Information will tell you which GPU you have. Unity doesn't require any specific hardware, but for the 3D environment you need a card that can do 3D acceleration (afaik). Get back to us with card you have and we'll let you know whether you'll get the full 3D in unity or not.

Of course, you can always install it and find out.

---

### Post by LewisGNoa on 2011-03-25
> System>Preferences>Hardware Information is there a terminal command for that, cuz, its not there (perhaps a diiferent name?) > Of course, you can always install it and find out.      You dont know how much crap installing ubuntu on this put me through

---

### Post by ShakeyJake on 2011-03-25
VGA Adapter:
```
lspci | grep VGA
```


Unity:
```
sudo apt-get install unity
```

---

### Post by LewisGNoa on 2011-03-25
Okay, when i type ```
 lspci >> terminal
``` terminal has the output: ```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U
```and when ```
lspci | grep VGA >> VGA
``` the VGA says ```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
```

---

### Post by LewisGNoa on 2011-03-25
It installs, but i have to load in as netbook. It takes a lot of time and cant do anything in Unity.

---

### Post by ShakeyJake on 2011-03-26
Hi Lewis, I'm by no means an expert on the ATI cards like yours but from what I understand it should work provided you have the [fglrx]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") driver. Please make sure though, like I said I'm hardly an expert and stick to nvidia when I can because of their vdpau technology.

---

### Post by wanderingarticfox on 2011-03-26
Just a side note you may want to invest in more RAM; 256KB is low these days; check with OEM maker for max your motherboard can handle and max it out. This should help with day to day everything.

---

### Post by LewisGNoa on 2011-05-23
Okay doesnt matter any more. This is now my expirental pc. I will use LFS, gentoo, and other things (like XNU). Not only does Unity not work, it is a piece of crap.

---

### Post by NormanFLinux on 2011-05-23
Unity 2D works fine. I think Canonical should ditch the 3D version. Do we really need fancy desktop effects? Compiz runs well even in a non-accelerated environment.

---

