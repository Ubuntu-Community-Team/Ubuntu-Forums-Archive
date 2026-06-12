---
title: "HELP! Dell Drivers and Modules!?"
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by commonslaughter on 2007-07-20
I just bought an Insperion 530 dual core, and I have a clean install of 7.04

BIG PROBLEM: I need a network driver to go online! Dell put the standard ethernet hardware in, but ubuntu is not recognizing it. HELP! I cant do ANYTHING until I can get the internet!

Thank you for your time.

---

### Post by lnknpk04 on 2007-07-20
What is the network card that you have?

---

### Post by commonslaughter on 2007-07-20
amaad@amaad-mainframe:~$ lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
**00:19.0 Ethernet controller: Intel Corporation Unknown device 10c0 (rev 02)**
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0423 (rev a1)
amaad@amaad-mainframe:~$ 

It is just the generic intel ethernet, as far as i can tell.

---

### Post by Seisen on 2007-07-20
This is what shows up on the Dell website 	```
825xx 10/100 Platform LAN Connect Device
``` 

I tried helping him but I couldn't find anything.

---

### Post by nnamod on 2007-07-20
Have you checked the output from dmesg? I have a Dell Poweredge 1900 and the network card was not detected. dmesg showed:

[42949382.930000] eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem f8000000, IRQ 169, node addr 00188b52be4a

So I put add eth to /etc/modules and configured the interface and it worked.

try to find a network device from that and add it to the modules file

---

### Post by mike999999 on 2007-07-21
[http://ubuntuforums.org/showthread.php?t=502058&highlight=530+network+card](http://ubuntuforums.org/showthread.php?t=502058&highlight=530+network+card)


:popcorn:

---

