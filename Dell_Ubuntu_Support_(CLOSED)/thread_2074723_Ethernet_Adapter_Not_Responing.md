---
title: "Ethernet Adapter Not Responing"
date: 2012-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yamat on 2012-10-22
Hello,

I have a Dell XPS M1210.  Ethernet adapter seems to be Broadcom Corporation BCM4401-B0 100Base-TX (rev 02).

When connect an ethernet wire with internet access, there seems to be no response whatsoever (lights on adapter itself not working and no connection established), whereas with same computer on Windows operating system (I used to have windows and switched to Ubuntu) adapter and connection worked fine.

Here is output of:

~:$ lspci | grep -i eth
Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

~:$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:8b:a4:7d:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

~:$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:a9:e2:e7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-17-generic firmware=15.32.2.9 ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:efdff000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:a4:7d:52
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

Could there be a problem with my driver?  Or could the driver somehow be blacklisted in /etc/modprobe.d/?

Any help would be much appreciated.

Kind regards.

---

### Post by buckyaustin on 2012-10-22
For some reason in the kernel a network boot is checked for first on the boot up. If this network boot fails sometimes the ethernet is disabled. While appearing to work. 

Go to your bios, and place network boot to the top of the boot list. Save and exit. This will cause your boot up to be about 3 seconds slower. Also you have to click [ctrl]+[c] to cancel the network boot each time. But this workaround has worked for me in the past and many others.

---

### Post by yamat on 2012-10-22
Many thanks for your help and prompt response - really appreciate.

I am afraid the suggested solution did not work.  I did the following:

(i) Went to system bios (by pressing function key F2 at bootup - this is what works for Dell XPS M1210).

(ii) Went to boot sequence, which looked like this:

          1. Discette Drive
          2. Internal HDD
          3. USB Storage Device
          4. CD/DVD/CD-RW Drive
          Onboard NIC

(iii) Moved Onboard NIC first in the list, and enabled it (by pressing Space), so now boot sequence looks like this:

          1. Onboard NIC
          2. Discette Drive
          3. Internal HDD
          4. USB Storage Device
          5. CD/DVD/CD-RW Drive

(iv) As you suggested, device slows boot time but still boots.  Yet even after boot, ethernet connection shows no sign of life.
 
Thanks much.

---

### Post by buckyaustin on 2012-10-23
Ok well undo what I previously stated. No point slowing your boot up if it doesn't work as a workaround anymore.

How long ago did you have Windows installed? No lights usually means hardware problem. Meaning the wire you are using could be damaged or the ethernet connection it self.

---

### Post by ALinuxWindowsBalance on 2012-10-23
Take out the onboard NIC.
And unless you plan to add another OS, take out everything else. his speeds up your boot time and prevents mistakes.
It worked for me, and if it didn't I wouldn't share it.
Actually, go to ADVANCED->And make sure the Onboard LAN is not [Disabled]

---

### Post by yamat on 2012-10-23
OK thanks to both for your responses and help.

I reverted back to previous boot sequence and disabled ones I do not use, as suggested by both.

Problem of-course still remains.  It used to work on Windows, which I completely deleted 5-6 weeks ago now, so I guess it may be a hardware issue after all.

By the way, not sure where Advanced is to check whether Onboard LAN is Not Disabled - note I am on Ubuntu 12.10.

Thanks for all help - much appreciate.

---

