---
title: "No internet on kubuntu"
date: 2010-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by akssps011 on 2010-08-29
Hi

I just installed kubuntu 10.04 on my dell N4010 laptop. 
The internet(ethernet) doesn't seem to work on my laptop. I looked at similar solution on the forum* [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) )
I don't have an internet connection so how can install build essential. Also build essential is not getting instaled from kubuntu 10.04 cd.

Moreover I found the result of a few commands different from the link given above, so I am posting them here

ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10584 (10.5 KB)  TX bytes:10584 (10.5 KB)
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

cat /etc/NetworkManager/nm-system-settings.conf
```
##some comments
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

dmesg | grep -e eth0 -e bcm
```
<No output>
```

lshw -C Network
```
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0300000-f0303fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f023ffff ioport:3000(size=128)
```

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]
02:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
04:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
05:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
```

Please help I am really stuck in this for over a week now.

---

### Post by mike909 on 2010-08-30
akss,
Follow my instructions here: [http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9)
I have same laptop, with both wired/wireless working. What I can't figure out is the headphone jack. Let me know if you every get that working.

---

### Post by varunendra on 2010-08-30
Interesting problem & interesting solution, and would be definitely interesting to see if it solves the problem for akss too.

I'll keep this thread & the linked one for my future reference. Thanks for sharing your experience Mike.

---

### Post by akssps011 on 2010-09-03
> **mike909 said:**
> akss,
Follow my instructions here: [http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9)
I have same laptop, with both wired/wireless working. What I can't figure out is the headphone jack. Let me know if you every get that working.

Thanks mike. that seems to be a reliable solution. I tried it (i got this version from there website: 1.0.1.13) and when I make I get this error

```
make -C ./src/ install
make[1]: Entering directory `/home/akssps011/AR81Family-linux-v1.0.1.13/src'
Makefile:61: *** Linux kernel source not found.  Stop.
make[1]: Leaving directory `/home/akssps011/AR81Family-linux-v1.0.1.13/src'
make: *** [install] Error 2
```

---

### Post by varunendra on 2010-09-03
Have you tried installing official drivers from Atheros? See [here]("http://ubuntuforums.org/showthread.php?p=9799566#post9799566") (refer to post #4).

---

### Post by akssps011 on 2010-09-18
the problem still persists. I downloaded the driver from [http://partner.atheros.com/Download.aspx?id=151](http://partner.atheros.com/Download.aspx?id=151) as well as the from the link you gave.

Meanwhile I have tried various OS : mandriva, ubuntu, kubuntu, fedora, debian, opensuse in past 1.5 week and only mandriva detected the driver( though other problems are there with mandriva). 
Please help, I have now no choice left but to use windows only.

---

### Post by mike909 on 2010-09-20
[http://ubuntuforums.org/showthread.php?t=1569966](http://ubuntuforums.org/showthread.php?t=1569966)
That should do the trick. First you get your wireless working, then apt-get install build-essential, then proceed to get your wired working.

---

