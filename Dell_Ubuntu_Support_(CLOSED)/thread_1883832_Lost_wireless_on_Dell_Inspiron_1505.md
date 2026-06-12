---
title: "Lost wireless on Dell Inspiron 1505"
date: 2011-11-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tornadoes28 on 2011-11-20
Lost wireless and can't figure out how to get back. I have Dell inspiron E1505. Browser froze so I did hard reboot. Now no wireless. Using 11.10.

---

### Post by empthollow on 2011-11-20
This may be an obvious question but I find it best to start with the basics.  Is the wireless switch turned on.  Sometimes when I hard reboot my laptop the wireless gets turned off and I need to switch it back on before I can get a network.  If this is not the problem post the output of 
```
ifconfig -a
```

---

### Post by tornadoes28 on 2011-11-20
I did that yesterday in Network settings it kept showing Airplane mode on and wireless off. I would turn Airplane mode off but the toggle for to turn wireless on never worked when I clicked on it. Always stayed off. Now today in Network setting, wireless is not even showing in the settings. I will post the results you asked for.

---

### Post by tornadoes28 on 2011-11-20
eth0      Link encap:Ethernet  HWaddr 00:19:b9:59:04:47  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe59:447/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:735192 (735.1 KB)  TX bytes:202800 (202.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 B)  TX bytes:700 (700.0 B)

---

### Post by empthollow on 2011-11-20
There is no wireless interface listed in your interfaces.  eth0 is your ethernet and lo is your loopback interface.  I suspect either there is a problem with the kernel module (driver), the wireless is off (which you've already checked), or the card itself is not working.  To test if the card is working I would suggest trying an older ubuntu live cd to test if it's working.  I suggest that because you have clearly had this working in the past and there may be a quirck in the current driver.

Please post the output of
```
lspci
```

---

### Post by tornadoes28 on 2011-11-20
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by linuxaddix on 2011-11-20
i have a dell e1505 and have had the same issue on some occasions.go to network settings and go to wireless.make sure to turn off airplane mode and then select wireless on.it might take a few tries then it works.

---

### Post by linuxaddix on 2011-11-20
oh and if you notice,fn+f2,turns it on and off also.it usually turns it off but not back on so dont play with that too much.you could try holding down f2.

---

### Post by tornadoes28 on 2011-11-20
I already checked network settings. I can turn off airplane mode but for some reason the wifi is not even in the setings anymore.

---

### Post by empthollow on 2011-11-20
The card shows in lscpi which means it is visible, which means little more than it exists and has some function, but the computer doesn't know what to do with it because it does not show in your ifconfig.  I would try reinstalling the kernel or modules for the broadcom card.

---

### Post by tornadoes28 on 2011-11-20
I got wireless to show up in Network settings again. Every time I open Network settings, it shows Airplane mode is on. Also, when I click to turn on wireless, the toggle does not turn on. It just keeps showing wireless is off.

---

### Post by ahmedtn on 2011-11-21
hi . i has this problem . u can simply connect ur dell to internet by a simple cable , then check the upgard u will find that the driver of ur wireless card is not installed . just install it and u will have ur wireless connection back :)  
i hope that helps u

---

### Post by tornadoes28 on 2011-11-21
Thanks but that does not fix it.
 
Does empthollow or anyone else have suggestions. I had wireless issues when I first installed 11.10 and followed instructions on this thread which fixed it originally, [http://ubuntuforums.org/showthread.php?t=1860327](http://ubuntuforums.org/showthread.php?t=1860327)

I've tried that again but it does not work.

When I right click on the network connection at the top, it says "wireless is disabled by hardware switch". Also, as I said, in Network settings, it shows wireless off and I can't turn it on. It also always shows airplane mode on.

Help please.

---

### Post by tornadoes28 on 2011-11-23
Hello? Any help? Thanks.

---

### Post by tornadoes28 on 2011-11-24
Does this tell you anything that can help. I still have no wireless.

eth0      Link encap:Ethernet  HWaddr 00:19:b9:59:04:47  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe59:447/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421755 (421.7 KB)  TX bytes:98471 (98.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 B)  TX bytes:500 (500.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:92:53:09:36  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by linuxaddix on 2011-11-27
turn airplane mode off and it should say wireless on if not like i said Fn+F2 turns it on and off.after enabling if no wireless connections show try a reboot.if your wifi light dont turn on before the login screen then you might have switch problems with your wifi.did you enable the b43 firmware and fwcutter?

---

### Post by linuxaddix on 2011-11-27
another thing you could try is the BIOS menu check to see if it is enabled in there also.

---

### Post by kapz on 2011-11-27
You can try blacklisting the acer_wmi module by adding an entry in /etc/modprobe.d/blacklist.conf file as follows:

blacklist acer_wmi

Save and close file, Reboot. Make sure your physical  switch is turned on. If it doesn't work then try this command: sudo rfkill unblock all

Still no luck..then post output of rfkill list and lsmod.

 Cheers!

---

