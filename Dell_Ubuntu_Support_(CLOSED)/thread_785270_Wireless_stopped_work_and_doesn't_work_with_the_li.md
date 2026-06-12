---
title: "Wireless stopped work and doesn't work with the live CD either"
date: 2008-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jpastore on 2008-05-07
I have a dell M90 that I recently upgraded to 8.04 and wireless stopped working. After spending some time on IRC and google I found that the iwl3945 driver just isn't working out for me and I can't seem to get the ndiswrapper working. Is there a way to forcefully load the ipw3945 driver until iwl3945 driver is fixed?

I installed wicd back in 7.10 because networkmanager was very flaky. The wicd isn't helping, nm is the same as it ever was...useless...

I'm trying to compile the driver found at Intel to see if that gets me anywhere...

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")

Some info about my system:

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G71 [Quadro FX 1500M] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

dmesg |grep 3945
```

[   25.936058] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   25.936062] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   25.937094] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   26.000936] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1c:23:0f:84:2e  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe0f:842e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1210033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1708687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:102740709 (97.9 MB)  TX bytes:1162899037 (1.0 GB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3876720 (3.6 MB)  TX bytes:3876720 (3.6 MB)

```

Any help would be greatly appreciated by a lot of people as it seems this is a very pervasive problem.

---

### Post by WanderingStar on 2008-05-07
Its very odd that the wlan0 is not shown in ifconfig.  Can you bring it up simply with:```
sudo ifup wlan0
```?

If this was an upgrade from Gutsy sometimes the udev enumeration becomes problematic.  Try moving the udev rule so it gets regenerated and hence re-enumerated.  You can do that with ```
sudo mv /etc/udev/rules.d/70-persistent-net.rules ~
``` Reboot after that an see if it comes up.  If so you can remove the file in your home directory (70-persistent-net.rules).  

Failing all of that you should be able to force the ipw driver by adding ```
blacklist iwl3945
``` to /etc/blacklist and adding ipw3945 to the end of /etc/modules.

Hopefully this gets you on the right path.  My 3945 wlan card works great in Hardy, but I did a clean install.

---

