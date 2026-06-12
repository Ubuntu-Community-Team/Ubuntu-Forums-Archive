---
title: "Wifi is not working"
date: 2010-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ummaneela on 2010-05-06
Hi everyone I am new to Ubuntu. I just downloaded Ubuntu 10.04 On my Dell Latitude D610 everything is working fine, only my wireless card is not working at all. I am new to Ubuntu so please help simplest way possible. Thanks everyone in advance.

---

### Post by pytheas22 on 2010-05-06
Please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lspci -nn
lsusb
dmesg | grep -e wlan
lshw -C Network
uname -rm
sudo iwlist scan
ifconfig
```

With that information we'll hopefully be able to figure out why the wireless isn't working, and figure out a solution.

---

### Post by my_linux on 2010-05-06
Unfortunately you've not said what WiFi card your D610 has*. I suggest you try the following:

1. Connect to the internet using Ethernet; ensure it's functioning.
2. Update Ubuntu using System > Administration > Update Manager.
3. Reboot after updating.
4. Go to System > Administration > Hardware drivers and follow instructions to install drivers if any related to WiFi.

*You should be able to determine what WiFi card you have installed by looking at lspci -v in terminal. If problems continue this info will be needed.

---

### Post by ummaneela on 2010-05-07
@ Pytheas22 
luthful@Luthful:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
luthful@Luthful:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
luthful@Luthful:~$ dmesg | grep -e wlan
luthful@Luthful:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:b6:5d:f5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a ip=192.168.0.4 latency=0 multicast=yes
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
luthful@Luthful:~$ uname -rm
2.6.32-21-generic i686
luthful@Luthful:~$ sudo iwlist scan
[sudo] password for luthful: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2010-05-07
Thanks for the information.  Most likely this is just a simple case of missing firmware.  You can install the firmware you need by plugging into the Internet and typing these commands (if it's impossible for you to plug in to get online, let me know and we can take a different approach):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

You will be asked if you want to download firmware automatically; say yes.  Then reboot and you should be all set.  If it still doesn't work after rebooting, please let me know the output of:
```

dmesg | grep -e b43 -e wlan
ls /lib/firmware
sudo iwlist scan
iwconfig
```

---

### Post by derekshaw on 2010-05-07
There appears to be an issue with the Canadian repository for 10.04 -- it's lacking the tools to get the Broadcom wireless chip working on an Acer Expire 3680.  I have 8.04 running nicely on 23 of these (after a doing what I am attempting here).  This is a test run -- bare metal install of Lucid Lynx from CD.


from dmseg
```
[   12.702753] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   12.702822] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   12.702884] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

from the quoted website
> The Broadcom wireless chip needs software, called "firmware", that runs on the wireless chip itself during operation. This firmware is copyrighted by Broadcom and must be extracted from Broadcom's proprietary drivers. To get such firmware on your system, you must download the driver from a legal distribution point, as noted below. Then you must extract the firmware from that Broadcom driver by using b43-fwcutter (or bcm43xx-fwcutter) and install it in the special directory for firmware - usually /lib/firmware. Please note that the firmware from the binary drivers is copyrighted by Broadcom Corporation and must not be redistributed. 

from the laptop
```
root@viwlaptop00:~# lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

root@viwlaptop00:~# b43-fwcutter
The program 'b43-fwcutter' is currently not installed.  You can install it by typing:
apt-get install b43-fwcutter

root@viwlaptop00:~# apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

```


Having had some (less-than-acceptable) results from the "server for canada" before, I changed the repository settings to point at [http://mirror.csclub.uwaterloo.ca/ubuntu](http://mirror.csclub.uwaterloo.ca/ubuntu)

and successfully installed b43-fwcutter

Hope this helps.

---

### Post by pytheas22 on 2010-05-07
**derekshaw**: thanks for the tip.  My guess, however, is that there's not a problem with the repository; you probably just needed to run "sudo apt-get update" before trying to download the b43-fwcutter package, in order to upgrade your software sources list.  Switching to a different repository would have necessitated an "apt-get update"; hence why it solved the problem.  I could be wrong, but I've never heard of an issue with a particular repository before.

Either way, I'm glad you figured it out.

---

### Post by ummaneela on 2010-05-08
@Pytheas22

luthful@Luthful:~$ dmesg | grep -e b43 -e wlan
luthful@Luthful:~$ ls /lib/firmware
2.6.32-21-generic         cpia2                     korg           sxg
2.6.32-22-generic         cxgb3                     libertas       tehuti
3com                      dabusb                    matrox         ti_3410.fw
acenic                    dsp56k                    mts_cdma.fw    ti_5052.fw
adaptec                   dvb-fe-xc5000-1.6.114.fw  mts_edge.fw    tigon
advansys                  dvb-usb-dib0700-1.20.fw   mts_gsm.fw     tr_smctr.bin
agere_ap_fw.bin           e100                      mwl8k          ttusb-budget
agere_sta_fw.bin          ea                        myricom        usbdux
aic94xx-seq.fw            edgeport                  NPE-B          usbduxfast_firmware.bin
ar9170-1.fw               emi26                     NPE-C          usbdux_firmware.bin
ar9170-2.fw               emi62                     ositech        v4l-cx231xx-avcore-01.fw
ar9170.fw                 ess                       ql2100_fw.bin  v4l-cx23418-apu.fw
ath3k-1.fw                i2400m-fw-usb-1.3.sbcf    ql2200_fw.bin  v4l-cx23418-cpu.fw
atmel_at76c502_3com.bin   i2400m-fw-usb-1.4.sbcf    ql2300_fw.bin  v4l-cx23418-dig.fw
atmel_at76c502.bin        intelliport2.bin          ql2322_fw.bin  v4l-cx2341x-dec.fw
atmel_at76c502d.bin       ipw2100-1.3.fw            ql2400_fw.bin  v4l-cx2341x-enc.fw
atmel_at76c502e.bin       ipw2100-1.3-i.fw          ql2500_fw.bin  v4l-cx2341x-init.mpg
atmel_at76c504_2958.bin   ipw2100-1.3-p.fw          qlogic         v4l-cx23885-avcore-01.fw
atmel_at76c504a_2958.bin  ipw2200-bss.fw            r128           v4l-cx23885-enc.fw
atmel_at76c504.bin        ipw2200-ibss.fw           radeon         v4l-cx25840.fw
atmel_at76c506.bin        ipw2200-sniffer.fw        rt2561.bin     v4l-pvrusb2-24xxx-01.fw
atmsar11.fw               iwlwifi-1000-3.ucode      rt2561s.bin    v4l-pvrusb2-29xxx-01.fw
av7110                    iwlwifi-3945-2.ucode      rt2661.bin     vicam
b43                       iwlwifi-4965-2.ucode      rt2860.bin     whiteheat.fw
b43legacy                 iwlwifi-5000-1.ucode      rt2870.bin     whiteheat_loader.fw
bnx2                      iwlwifi-5000-2.ucode      rt73.bin       yam
bnx2x-e1-4.8.53.0.fw      iwlwifi-5150-2.ucode      RTL8192SE      yamaha
bnx2x-e1-5.2.7.0.fw       iwlwifi-6000-4.ucode      sb16           zd1201-ap.fw
bnx2x-e1h-4.8.53.0.fw     kaweth                    scripts        zd1201.fw
bnx2x-e1h-5.2.7.0.fw      keyspan                   slicoss        zd1211
cis                       keyspan_pda               sun
luthful@Luthful:~$ sudo iwlist scan
[sudo] password for luthful: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

luthful@Luthful:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2010-05-09
**ummaneela**: that's strange; sorry installing the firmware didn't sort it out.  It could be the case that the module is not loading for some reason.  What output do you get if you type:
```

sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43
lshw -C Network
sudo iwlist scan
dmesg | grep -e b43 -e wlan -e ssb
```

---

### Post by ummaneela on 2010-05-09
Thank you very much Pytheas 22 for your help.

luthful@Luthful:~$ sudo rmmod b43
luthful@Luthful:~$ sudo rmmod ssb
luthful@Luthful:~$ sudo modprobe b43
luthful@Luthful:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:b6:5d:f5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a ip=192.168.0.4 latency=0 multicast=yes
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:32:4e:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
luthful@Luthful:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
                                                                                                                                               
eth0      Interface doesn't support scanning.                                                                                                  
                                                                                                                                               
pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:37:0C:85:70
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"qwest0128"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000872d2e986f1
                    Extra: Last beacon: 1060ms ago
                    IE: Unknown: 0009717765737430313238
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:22:75:D3:0C:D6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key on
                    ESSID:"Baas' Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000002ca5eb615c
                    Extra: Last beacon: 1292ms ago
                    IE: Unknown: 000D4261617327204E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010775B6680BFDE11D38D2F002275D30CD6103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010014127A
                    IE: Unknown: DD1E00904C33EE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050400000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 03 - Address: 00:24:7B:01:d9:42
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key on
                    ESSID:"myqwest1153"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000084d7740224d
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 000B6D79717765737431313533
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1E:A7:8D:C8:8C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key on
                    ESSID:"myqwest1917"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003d014d97249
                    Extra: Last beacon: 364ms ago
                    IE: Unknown: 000B6D79717765737431393137
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
          Cell 05 - Address: 00:1E:C7:96:50:31
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key on
                    ESSID:"2WIRE801"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001778842d306
                    Extra: Last beacon: 584ms ago
                    IE: Unknown: 00083257495245383031
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:24:7B:0E:C8:40
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key on
                    ESSID:"myqwest8767"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003bdf4478249
                    Extra: Last beacon: 3788ms ago
                    IE: Unknown: 000B6D79717765737438373637
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:23:75:26:47:D0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key on
                    ESSID:"qwest8384(young)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000197d7d1ce
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 001071776573743833383428796F756E6729
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 050C010200000000000000000000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

luthful@Luthful:~$ dmesg | grep -e b43 -e wlan -e ssb^C
luthful@Luthful:~$

---

### Post by pytheas22 on 2010-05-09
It looks like you're able to scan for networks now, which is definitely good progress.  Did you try connecting to any and did it work?  You should be able to connect now simply by left-clicking on the NetworkManager applet in the upper-right corner of your screen and selecting the name of your wireless network.

Also, if you find your wireless not working after reboots, let me know.  We may need to write a short boot script to take care of some issues relating to this.  For the time being, however, if you can't see networks at all, the following commands should be enough to fix it:
```

sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43
```

---

