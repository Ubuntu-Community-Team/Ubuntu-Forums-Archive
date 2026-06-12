---
title: "Slow login"
date: 2010-12-07
forum: Desktop Environments
---

### Post by srivo on 2010-12-07
This doesn't happen every logging but some time the logging process can take up to 5 minute. Right after I enter the password the computer freeze and only the mouse work.

This also happen when I login after the screensaver is in action. If I enter the wrong password. The same thing will happen. Computing will take 5 minutes before telling me that I enter the wrong password.

Anyone having the same issue?

---

### Post by appzone on 2010-12-07
> **srivo said:**
> This doesn't happen every logging but some time the logging process can take up to 5 minute. Right after I enter the password the computer freeze and only the mouse work.

This also happen when I login after the screensaver is in action. If I enter the wrong password. The same thing will happen. Computing will take 5 minutes before telling me that I enter the wrong password.

Anyone having the same issue?

what? 5 minutes?
i just have about 5 - 10 seconds to login 
is it your fresh install ubuntu??
oh yea, what version do you have?

---

### Post by srivo on 2010-12-08
I use 10.04 64 bit, with the kernel Server. I use that machine more like a server and for VM.

I think it a fresh install but I don't remember exactly if I upgrade from 9.1 or simply did a fresh install. It's running since mid may!

Here is the uname -a output
```

Linux julia 2.6.32-26-server #48-Ubuntu SMP Wed Nov 24 10:28:32 UTC 2010 x86_64 GNU/Linux

```

---

### Post by coffeecat on 2010-12-08
Do you have any extra or unusual hardware installed? When I fitted a TV tuner PCI card to one of my machines the login screen would hang for about a minute - but not as long as 5 minutes.

---

### Post by srivo on 2010-12-08
None,

I was having 2 NIC and remove one after having a network problem. The slow login happen soon after that.

Here is the lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
07:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```

---

### Post by BorisPlankton on 2010-12-12
I have same issue and it does take a good 5 minutes maybe longer. The first login is fine. It is after the PC sleeps and you next need to enter login.
This seemed to occur after I encrypted folder but that might be coincidence. Ubunutu 10.04 LTS Lucid Lynx.

---

