---
title: "Wireless Dell Wimax/Wifi 6050"
date: 2010-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by basher5_2 on 2010-09-03
So Ive found a couple of people with the same problems in the forums but haven't found a good solution/guide to help me fix it.
My wireless always says disconnected, and the hotkey or trying to make it go up in the terminal don't work. From other people it looks like the driver is missing 
Any pointers to a good guide or thread would be nice 
The output of lspci
...
07:00.0 Network controller: Intel Corporation WiMAX/Wifi Link 6050 Series (rev 57)
...

Thanks

---

### Post by Tracy177 on 2010-09-03
> **basher5_2 said:**
> So Ive found a couple of people with the same problems in the forums but haven't found a good solution/guide to help me fix it.
My wireless always says disconnected, and the hotkey or trying to make it go up in the terminal don't work. From other people it looks like the driver is missing 
Any pointers to a good guide or thread would be nice 
The output of lspci
...
07:00.0 Network controller: Intel Corporation WiMAX/Wifi Link 6050 Series (rev 57)
...

Thanks


check up if the network button is on in your laptop if it is laptop

if it is on 

second u could check up yourself dmesg or paste output here



i there is firmware missing u need to get it install it or put it in your home/firmwares

---

### Post by basher5_2 on 2010-09-03
[    9.420312] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.420322] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.420933] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.420979] iwlagn 0000:07:00.0: setting latency timer to 64
[    9.421105] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[    9.442872] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.442955]   alloc irq_desc for 29 on node -1
[    9.442961]   alloc kstat_irqs on node -1
[    9.442989] iwlagn 0000:07:00.0: irq 29 for MSI/MSI-X
[    9.668894] cfg80211: World regulatory domain updated:
[    9.668902]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.668910]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.668916]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.668922]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.668928]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.668934]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.203369] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.875439]   alloc irq_desc for 22 on node -1
[   10.875446]   alloc kstat_irqs on node -1
[   10.875460] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.875527] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.996930] hda_codec: ALC272: BIOS auto-probing.
[   10.998659] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   12.324047] r8169: eth0: link down
[   12.324456] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.346874] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   12.349687] type=1505 audit(1283558028.080:5):  operation="profile_replace" pid=847 name="/sbin/dhclient3"
[   12.350237] type=1505 audit(1283558028.080:6):  operation="profile_replace" pid=847 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.350540] type=1505 audit(1283558028.080:7):  operation="profile_replace" pid=847 name="/usr/lib/connman/scripts/dhclient-script"
[   12.522747] type=1505 audit(1283558028.251:8):  operation="profile_load" pid=850 name="/usr/bin/evince"
[   12.529310] type=1505 audit(1283558028.260:9):  operation="profile_load" pid=850 name="/usr/bin/evince-previewer"
[   12.533557] type=1505 audit(1283558028.264:10):  operation="profile_load" pid=850 name="/usr/bin/evince-thumbnailer"
[   12.555016] iwlagn 0000:07:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   12.555033] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   12.559684] iwlagn 0000:07:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   12.559700] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   12.564187] iwlagn 0000:07:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   12.564202] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   12.569104] iwlagn 0000:07:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   12.569115] iwlagn 0000:07:00.0: Could not read microcode: -2
[   12.648981] type=1505 audit(1283558028.379:11):  operation="profile_load" pid=854 name="/usr/lib/cups/backend/cups-pdf"
[   12.971608] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   12.975447] iwlagn 0000:07:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   12.975463] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   12.980769] iwlagn 0000:07:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   12.980781] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   12.985867] iwlagn 0000:07:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   12.985882] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   12.991806] iwlagn 0000:07:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   12.991819] iwlagn 0000:07:00.0: Could not read microcode: -2


that looks like the important part, it looks like it is missing the firmware which I think you can get off the intel site, I just need to know how to install it/where to put it.

Thanks

---

### Post by basher5_2 on 2010-09-03
ok so I got the firmware installed and restarted my computer. It now finds the networks but when I try to connect to them it doesn't. Any other other suggest, let me know if you need more info from my computer

---

### Post by Baji P. on 2010-09-04
Which version of Ubuntu are you running ?

I have found that the best way to get wireless working with stable connections is to install from scratch in expert mode (hit F6 on install screen) using the alternate CD, with the machine connected to the internet using your wired ethernet port.

Make sure you select every package repository that is available when asked.

During the installation the installer will go online and find the best drivers available for your hardware.

---

### Post by basher5_2 on 2010-09-05
I am using netbook remix, is there an alternate install for that?

---

### Post by Baji P. on 2010-09-06
Sorry, I didn't realize you were on a netbook. I don't think there is an alternate install for the netbook remix.

Time permitting I would try both the remix and the standard alternate install on the netbook. No matter with distro or CD you are using, make sure you are connected by a wired ethernet during the install itself.

---

### Post by NathanBrauer on 2010-12-02
Hey there, I'm not sure if you're still having the issue, but I just got a new laptop with the same hardware and I just found the solution:

[LIST=1]
[*]Go to 
[*]Download "iwlwifi-6050-ucode-9.201.4.1.tgz"
[*]Extract the archive
[*]in terminal: ```
cd /path/to/folder
```
[*]Copy it over to the firmware directory ```
sudo cp iwlwifi-6050-4.ucode /lib/firmware/iwlwifi-6050-4.ucode
```
[*]Right-click the network indicator and uncheck "Enable Wireless" (this will disable it) then repeat to reenable it.  Wait a few seconds and I should find networks - if it doesn't, log out then log back in and you should be good to go.
[/LIST]

Happy Birthday & Merry Christmas! :)

---

### Post by outskut on 2011-03-07
I'm not sure if this would be different for a netbook, but I've had a problem installing this wifi card on every distribution I've tried so far, and it's this thread that has solved the problem for me:
[http://ubuntuforums.org/showthread.php?t=1645370](http://ubuntuforums.org/showthread.php?t=1645370)

just replace moudules with modules in the package reference - it's a typo

---

