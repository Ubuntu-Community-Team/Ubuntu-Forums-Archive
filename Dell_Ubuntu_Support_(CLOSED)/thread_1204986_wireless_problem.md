---
title: "wireless problem"
date: 2009-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by moonliter on 2009-07-05
I installed dell ubuntu 9.04 on dell vostro 1710 and can not connect to wireless when I type in command ifconfig it says something no extensions i dont have problem in windows vista also there is no blinking lid when I turn on wireless Please help
 my wireless card is Dell Wireless 1505 Draft 802.11n WLAN Mini-Card

---

### Post by pytheas22 on 2009-07-05
Please open a terminal from the Applications>Internet menu, run the following commands and post the output here:
```

lspci -nn
lshw -C Network
uname -rm
dmesg | grep -e wlan -e b43 -e iwl
```

That will provide the information necessary to figure out what's wrong.

---

### Post by moonliter on 2009-07-05
lcpci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) 
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GS [10de:0425] (rev a1) 
06:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03) 
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02) 
08:05.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02) 
08:05.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02) 
08:05.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01) 
moonliter@dell-desktop:~$ lshw -C Network  
WARNING: you should run this program as super-user. 
  *-network                
       description: Network controller 
       product: BCM4328 802.11a/b/g/n 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: 03 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:21:70:da:e0:9d 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 8e:d5:02:4a:90:dc 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
moonliter@dell-desktop:~$ uname -rm  
2.6.28-11-generic i686 
moonliter@dell-desktop:~$ dmesg | grep -e wlan -e b43 -e iwl 
[    5.292783] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    5.292797] b43-pci-bridge 0000:06:00.0: setting latency timer to 64 
moonliter@dell-desktop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) 
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GS [10de:0425] (rev a1) 
06:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03) 
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02) 
08:05.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02) 
08:05.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02) 
08:05.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01) 

root@dell-desktop:/home/moonliter# lshw -C Network  
  *-network                
       description: Network controller 
       product: BCM4328 802.11a/b/g/n 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: 03 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:21:70:da:e0:9d 
       size: 10MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 8e:d5:02:4a:90:dc 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 



root@dell-desktop:/home/moonliter# uname -rm  
2.6.28-11-generic i686 

root@dell-desktop:/home/moonliter# dmesg | grep -e wlan -e b43 -e iwl 
[    5.292783] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    5.292797] b43-pci-bridge 0000:06:00.0: setting latency timer to 64

---

### Post by pytheas22 on 2009-07-05
Please run these commands, and post the output:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe wl
sudo iwlist scan
dmesg | grep -e wl -e wlan
```

At this point, your wireless should hopefully be working.  If it is, please try connecting.  If not, please just post the output from these commands.

---

### Post by moonliter on 2009-07-05
moonliter@dell-desktop:~$ sudo rmmod b43

ERROR: Module b43 does not exist in /proc/modules

moonliter@dell-desktop:~$ sudo rmmod b44

ERROR: Module b44 does not exist in /proc/modules

moonliter@dell-desktop:~$ sudo rmmod ssb

ERROR: Module ssb does not exist in /proc/modules

moonliter@dell-desktop:~$ sudo modprobe wl

moonliter@dell-desktop:~$ 
 notting




moonliter@dell-desktop:~$ sudo modprobe wl

moonliter@dell-desktop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



pan0      Interface doesn't support scanning.



eth1      Scan completed :

          Cell 01 - Address: 00:02:6F:47:21:07

                    ESSID:"point"

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:4/5  Signal level:-62 dBm  Noise level:-82 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

          Cell 02 - Address: 00:1D:0F:B9:D9:F4

                    ESSID:"moba.hotspot.19"

                    Mode:Managed

                    Frequency:2.432 GHz (Channel 5)

                    Quality:1/5  Signal level:-87 dBm  Noise level:-87 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

          Cell 03 - Address: 02:1D:0F:B9:D9:F4

                    ESSID:"moba.hotspot"

                    Mode:Managed

                    Frequency:2.432 GHz (Channel 5)

                    Quality:1/5  Signal level:-86 dBm  Noise level:-87 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

moonliter@dell-desktop:~$ dmesg | grep -e wl -e wlan

[  476.404708] wl 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[  476.404726] wl 0000:06:00.0: setting latency timer to 64

---

### Post by pytheas22 on 2009-07-05
It looks like your wireless interface was brought up successfully and you can see networks.  Are you able to connect?

(If you're rebooted your computer in the last twenty minutes, you will need to run the commands form post #4 again for the card to start working--once we determine that this definitely fixes the problem, we can make the change permanent, but for now you would have to repeat those commands after each reboot.)

---

### Post by moonliter on 2009-07-06
ok I made it Thanks a lot and please post when problem is fixed

---

### Post by pytheas22 on 2009-07-06
> ok I made it Thanks a lot and please post when problem is fixed

I'm confused.  Are you able to connect now?  Do you need more help?  If you want to make the fix permanent, so that you don't have to run all those commands manually each time you reboot your computer, let me know.

---

### Post by moonliter on 2009-07-06
Yes everything is ok I am connected but have to always run those commands each time I reboot Can you help?

---

### Post by pytheas22 on 2009-07-06
To make the commands run automatically each time you boot, run this set of commands once:

```
sudo -s
echo -e "#!/bin/bash\nsudo rmmod b43\nsudo rmmod b44\nsudo rmmod ssb\nsudo modprobe wl" > /etc/init.d/wifi-fix.sh
cd /etc/init.d
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults
```

This will create a start-up script that will execute those commands automatically.  After you've created the script, reboot, and the wireless should be working without you having to enter any commands.  If it's not, let me know.

---

### Post by moonliter on 2009-07-13
ok  I got this after run

sudo -s
root@dell-desktop:~# echo -e "#!/bin/bash\nsudo rmmod b43\nsudo rmmod b44\nsudo rmmod ssb\nsudo modprobe wl" > /etc/init.d/wifi-fix.sh
bash: !/bin/bash\nsudo: event not found
root@dell-desktop:~# cd /etc/init.d
root@dell-desktop:/etc/init.d# chmod +x wifi-fix.sh
chmod: cannot access `wifi-fix.sh': No such file or directory
root@dell-desktop:/etc/init.d# update-rc.d wifi-fix.sh defaults
update-rc.d: /etc/init.d/wifi-fix.sh: file does not exist

---

### Post by pytheas22 on 2009-07-13
Sorry, there was a typo in the commands I asked you to run--the second line should have used single quotes, not double.  Please try this:
```

sudo -s
echo -e '#!/bin/bash\nsudo rmmod b43\nsudo rmmod b44\nsudo rmmod ssb\nsudo modprobe wl' > /etc/init.d/wifi-fix.sh
cd /etc/init.d
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults
```

That should work better.

---

### Post by moonliter on 2009-07-13
yeah problem is fixed now Thank you for your help We can lock this conversation!!:guitar::lolflag:):P

---

### Post by photographerHU on 2009-07-28
Hi,
I can say thank you too, because its working, but I still have one question: How can I change back to cable internet? (I plug in the cable and nothing, disable wireless with right click: no internet, but the cable is still in.) So how can I use cable internet now?
Maybe I just missed something. 
OR IF NO solution 4 this: how can I change back, to type after every  boot in (do not run it automatically)...... So how can I cancel this: 
sudo -s
echo -e '#!/bin/bash\nsudo rmmod b43\nsudo rmmod b44\nsudo rmmod ssb\nsudo modprobe wl' > /etc/init.d/wifi-fix.sh
cd /etc/init.d
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults 
Please help me.

---

### Post by photographerHU on 2009-07-28
It looks like not able to see the cable internet....

---

### Post by pytheas22 on 2009-07-28
photographerHU: to enable the ethernet, it should work to type:
```

sudo modprobe b44
sudo ifconfig eth0 up
```

Then try connecting.  This may break your wireless, however; I'm not sure.  If it does break wireless, run these commands again to get it back:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe wl
```

The problem is caused because the ethernet driver for Broadcom-based chips, 'b44', conflicts with the wireless driver 'wl'.

---

### Post by photographerHU on 2009-07-29
Than you. 
I will try it.

---

### Post by photographerHU on 2009-07-29
ohh sorry. One more thing:
Do you know how to use Aircrack? ((OR something like that) it looks like it isnt supported) I cant find any good news with 1505 Draft 802.11n

---

### Post by pytheas22 on 2009-07-29
Aircrack won't work with the 'wl' driver (at least, you won't be able to inject; you may be able to sniff but I'm not sure).  It works with the 'b43' driver that supports most Broadcom-based cards (yours is Broadcom), but the last time I checked, b43 still doesn't work with 802.11n devices.  This means there's no support for aircrack on the Broadcom 802.11n cards at the moment, as far as I know.

---

### Post by photographerHU on 2009-07-29
Hi,

  This means I need to buy an external, USB wireless? Can I do it in other ways? Virtual?

---

### Post by pytheas22 on 2009-07-29
I'm not an expert on aircrack, but yes, I think your only option at this point is to buy a new wireless card with a chipset that supports injection.  You might want to ask in the aircrack forums to be sure.

You could also wait and hope that the b43 people expand support to 802.11n devices soon.  I'm not sure what their plans are in that regard but you could check their website too.

---

### Post by photographerHU on 2009-07-30
I searched a little bit and I found this:
[http://backtrack.offensive-security.com/index.php/HCL:Wireless#Notes_for_broadcom_owners](http://backtrack.offensive-security.com/index.php/HCL:Wireless#Notes_for_broadcom_owners)
(there they offer for BCM4328 this driver: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) )
Did you hear anything about this driver?
AND this:
[http://forum.aircrack-ng.org/index.php?topic=3597.0](http://forum.aircrack-ng.org/index.php?topic=3597.0) (but this one just for Ubuntu 8.04).............
Im kind of new so I just dont want to try them out until, when Im not sure that is working 4 me and how to...

---

### Post by pytheas22 on 2009-07-30
The linux_sta driver is the one you're using now.  Its module is named 'wl'.  It doesn't support aircrack.

The 'b43' driver does support aircrack, but I don't think it will work with your model of wireless card.

---

### Post by photographerHU on 2009-07-31
Ohh ok. But thank you. So I think I will buy a usb one....

---

