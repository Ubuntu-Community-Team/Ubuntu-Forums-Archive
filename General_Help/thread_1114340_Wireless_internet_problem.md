---
title: "Wireless internet problem"
date: 2009-04-02
forum: General Help
---

### Post by Eagles18 on 2009-04-02
Hi,I just installed Ubuntu and I'm loving it,exept the fact that my internet is not working.I believe it has something to do with the drivers.I have a laptop and the wifi light is not turning blue(blue=wifi enabled).I like Ubuntu,but a computer is not a computer without internet.Can someone help me?I've been searching for about 2 days now. Thanks

---

### Post by coffeecat on 2009-04-02
Welcome to the forum. As it's such a big forum, you probably haven't found [this sticky]("http://ubuntuforums.org/showthread.php?t=370108") yet. Have a look at the 'How to Post a Wireless Issue' link in that, so that you can post information that will be needed for people to help you.

**Edit:** actually that link is a bit daunting for a newcomer to Linux. At least give us some information about the make/model of machine, and open a terminal (Applications > Accessories > Terminal), and type

```
lspci
```

and post the output. You'll need to copy and paste. :wink:

---

### Post by The Shin on 2009-04-02
What I did was just make the settings for the connection and reboot. Did you reboot?

---

### Post by coffeecat on 2009-04-02
Well, there's a thought - it might be something simple.

**Eagles18**. In the upper panel is an icon that looks like 2 computers. If you're not connected to the internet, it will show a little white on red x. Simply click on that icon. If the drivers for your wireless chipset are installed, a list of all detectable wireless networks should drop down. Simply click on yours and enter your passkey where prompted.

Yes, I know you've been searching for 2 days, but there's a lot of outdated stuff on the internet, and also unnecessarily geeky howtos.

---

### Post by Eagles18 on 2009-04-02
> **coffeecat said:**
> Welcome to the forum. As it's such a big forum, you probably haven't found [this sticky]("http://ubuntuforums.org/showthread.php?t=370108") yet. Have a look at the 'How to Post a Wireless Issue' link in that, so that you can post information that will be needed for people to help you.

**Edit:** actually that link is a bit daunting for a newcomer to Linux. At least give us some information about the make/model of machine, and open a terminal (Applications > Accessories > Terminal), and type

```
lspci
```

and post the output. You'll need to copy and paste. :wink:


This is what I got:

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Device 0845 (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by coffeecat on 2009-04-02
Which version of Ubuntu have you installed? 8.04, 8.10 or 9.04Beta? If 8.10, check out the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810"), particularly:

> 
**Atheros ath5k wireless driver not enabled by default**

  The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation.
I don't know whether the ath5k driver is relevant for your particular Atheros chipset; others might be able to help.

---

### Post by coffeeaddict22 on 2009-04-02
Hi Eagles18,

See if you've got a driver installed.  Find the terminal again, and try 
```
lshw -C network
```

post the bit that starts with ```
  *-network               
       description: Wireless interface
```
back.

In case you wondered, lshw ListS HardWare; the -C network makes it spit out only the lines relating to your network interface.

And re the previous post, if you aren't sure, ```
cat /etc/issue
``` will tell you which version of Ubuntu you're on.

---

### Post by Eagles18 on 2009-04-02
I'm currently using Ubuntu 8.10.The driver is enabled,but I don't think it is working.BTW,it is not that I don't know how to connect to the internet,it is that my wifi is not working,but it works when I'm on windows vista(which is how I'm typing this)
This is really ruining Ubuntu for me :(

---

### Post by Eagles18 on 2009-04-02
No one knows how to fix this?...Ubuntu is such a letdown

---

### Post by coffeeaddict22 on 2009-04-02
WE don't know you've got a driver installed, and you haven't told us how you know you have.  If you have, there's other steps to try, but the driver is the problem usually, so prove it's present and working first.  If you assume (= ***/U/ME) the driver is present and go hunting network problems, it's a long and pointless day.

 So, find the terminal again, and type 
```
lshw -C network
```


post the bit that starts with
Code:
```
*-network               
       description: Wireless interface

```
  
back.

---

### Post by Eagles18 on 2009-04-02
> **coffeeaddict22 said:**
> WE don't know you've got a driver installed, and you haven't told us how you know you have.  If you have, there's other steps to try, but the driver is the problem usually, so prove it's present and working first.  If you assume (= ***/U/ME) the driver is present and go hunting network problems, it's a long and pointless day.

 So, find the terminal again, and type 
```
lshw -C network
```


post the bit that starts with
Code:
```
*-network               
       description: Wireless interface

```
  
back.

NVM,I'll just stick to Windows Vista :guitar:

---

