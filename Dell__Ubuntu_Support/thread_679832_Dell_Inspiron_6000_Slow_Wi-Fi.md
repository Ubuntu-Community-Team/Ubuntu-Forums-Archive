---
title: "Dell Inspiron 6000 Slow Wi-Fi"
date: 2008-01-27
forum: Dell  Ubuntu Support
---

### Post by WeRReD on 2008-01-27
Hi. 
I'm running Ubuntu 7.10 on a Dell Inspiron 6000 laptop and have a strange problem.
I've installed a wireless router (D-Link DI-524), connecting to it well, but the wifi speed is really slow. When nothing transferring the pings to my router are about 7-9ms and when trying to open a webpage (google for example) the pings jump up to 700-800ms. Many packets are lost during the ping process. 

Downloads are no more than 28k/s, which is a huge difference if I download something during 

I have another Windows laptop which connects to the router really well through the wifi. Pings are no more than 2-3ms and the internet is running smoothly. 

I've googled the problem a lot and all I've found was a problem with a Broadcom chipset, which isn't my case.

Here is the output of my lspci command: 
> oot@werred-laptop:/home/werred/misc# lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)



Here is my ping 192.168.0.1 result:
> 
64 bytes from 192.168.0.1: icmp_seq=113 ttl=64 time=1939 ms
64 bytes from 192.168.0.1: icmp_seq=114 ttl=64 time=2041 ms
64 bytes from 192.168.0.1: icmp_seq=115 ttl=64 time=1757 ms
64 bytes from 192.168.0.1: icmp_seq=116 ttl=64 time=1662 ms
64 bytes from 192.168.0.1: icmp_seq=117 ttl=64 time=1025 ms
64 bytes from 192.168.0.1: icmp_seq=118 ttl=64 time=945 ms
64 bytes from 192.168.0.1: icmp_seq=119 ttl=64 time=767 ms
64 bytes from 192.168.0.1: icmp_seq=120 ttl=64 time=1513 ms
64 bytes from 192.168.0.1: icmp_seq=121 ttl=64 time=2002 ms
64 bytes from 192.168.0.1: icmp_seq=122 ttl=64 time=2343 ms
64 bytes from 192.168.0.1: icmp_seq=123 ttl=64 time=1978 ms
64 bytes from 192.168.0.1: icmp_seq=124 ttl=64 time=1605 ms
64 bytes from 192.168.0.1: icmp_seq=125 ttl=64 time=1286 ms
64 bytes from 192.168.0.1: icmp_seq=126 ttl=64 time=986 ms
64 bytes from 192.168.0.1: icmp_seq=127 ttl=64 time=1023 ms
64 bytes from 192.168.0.1: icmp_seq=128 ttl=64 time=1094 ms
64 bytes from 192.168.0.1: icmp_seq=129 ttl=64 time=989 ms
64 bytes from 192.168.0.1: icmp_seq=130 ttl=64 time=1242 ms
64 bytes from 192.168.0.1: icmp_seq=131 ttl=64 time=1404 ms
64 bytes from 192.168.0.1: icmp_seq=132 ttl=64 time=1275 ms
64 bytes from 192.168.0.1: icmp_seq=133 ttl=64 time=1332 ms
64 bytes from 192.168.0.1: icmp_seq=134 ttl=64 time=1747 ms
64 bytes from 192.168.0.1: icmp_seq=135 ttl=64 time=1489 ms
64 bytes from 192.168.0.1: icmp_seq=136 ttl=64 time=1732 ms
64 bytes from 192.168.0.1: icmp_seq=137 ttl=64 time=1157 ms
64 bytes from 192.168.0.1: icmp_seq=138 ttl=64 time=850 ms


As you can see that is pretty horrible

And the output of iwconfig:
> werred@werred-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XpoMaNet"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:5B:E6:05:72
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-37 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:9  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:8

Any help on this one is really appreciated. 

Thanks.

---

### Post by ghost_ryder35 on 2008-01-27
in my experience 7.10 really hates a defualt gateway of 192.168.0.1, change your routers ip address to 192.168.1.100,  Every machine I have installed 7.10 on (5 of them) so far has had the same problem and all of the routers were using the 192.168.0.1 address.  Everytime I have changed it to 192.168.1.100 it fixes the problem.  Try this I know it sounds strage but it will probally work :)

---

### Post by WeRReD on 2008-01-28
> **ghost_ryder35 said:**
> in my experience 7.10 really hates a defualt gateway of 192.168.0.1, change your routers ip address to 192.168.1.100,  Every machine I have installed 7.10 on (5 of them) so far has had the same problem and all of the routers were using the 192.168.0.1 address.  Everytime I have changed it to 192.168.1.100 it fixes the problem.  Try this I know it sounds strage but it will probally work :)

No, it didn't help. The problem persists...

---

