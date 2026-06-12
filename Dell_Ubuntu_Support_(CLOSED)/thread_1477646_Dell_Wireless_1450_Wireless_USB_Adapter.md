---
title: "Dell Wireless 1450 Wireless USB Adapter"
date: 2010-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raysaun on 2010-05-09
I upgraded from 9.10 to 10.04 today. Wireless worked perfectly before the upgrade. I don't think that my wireless card is even recognized now.

Based on some other posts that I've seen, perhaps these commands will provide clues? (Sorry for my newbishness!)

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82925X/XE Memory Controller Hub [8086:2584] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82925X/XE PCI Express Root Port [8086:2585] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller [8086:2652] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]
01:00.1 Display controller [0380]: ATI Technologies Inc RV370 [Radeon X300SE] [1002:5b70]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
04:01.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)
04:02.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
04:02.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
04:02.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04)




iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by totziens on 2010-05-09
Have you tried the following?

Go to:
System -> Administration -> Hardware Drivers -> look for "Broadcom STA Wireless driver" and activate it.

It used to work for me using the same model of laptop as yours until I upgrade to Linux 2.6.32.22-generic :(

---

### Post by raysaun on 2010-05-09
> **totziens said:**
> Have you tried the following?
 
Go to:
System -> Administration -> Hardware Drivers -> look for "Broadcom STA Wireless driver" and activate it.
 
It used to work for me using the same model of laptop as yours until I upgrade to Linux 2.6.32.22-generic :(
 
Thanks for your reply, totziens!
 
When I go to System -> Administration -> Hardware Drivers, after searching for drivers, I get a dialog that is empty except for the statement that there are no proprietary drivers were found on the machine.

---

### Post by Sintar on 2010-05-15
so i'm assuming that you want the native drivers not a ndis wrapper. that you have a usb wifi adapter 1450. not a 1450 studio laptop.

first off go to this web site 

[http://daemonizer.de/prism54/prism54-fw/](http://daemonizer.de/prism54/prism54-fw/)

download a firmware for your device i would suggest one from the usb list twords the bottom they probably  have less bugs

1st gen device get a firmware ending in lm86.arm

2nd gen device get one ending in lm87.arm

 i used the very bottom one from the usb section since i have a second  gen device now rename the firmware you downloaded to

isl3886usb for the 1st gen or

isl3887usb for the 2nd gen

now move it to 

/lib/firmware/"YOUR_KERNEL_VER_HERE"/"YOUR DOWNLOADED FIRMWARE HERE"

for 64 bit you might as well put one here too 

/lib64/firmware/"YOUR_KERNEL_VER_HERE"/"YOUR DOWNLOADED FIRMWARE HERE"

the syntax to move is

 sudo mv /Source/directory/filename /dest/dir/filename

once the files are moved

run 

modprobe -r p54usb | modprobe -r p54common

then

modprobe  p54usb | modprobe p54common


now iwconfig 
it should list your adapter then connect and have a good day

---

