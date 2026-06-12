---
title: "Internet Not working"
date: 2009-03-10
forum: General Help
---

### Post by Sadiztik on 2009-03-10
Yo whatup?
Okay so i just installed Ubuntu on my Gateway FX laptop. I had Windows Ultimate 64-bit. I uninstalled it and installed Ubuntu 8.10 Desktop i386 and i cant connect to the internet via my wireless router. I'm very new to linux based systems used Windows my whole life. Can anybody help me figure out how to navigate ubuntu correctly and help me figure out how to set up the internet. Thank you

Sadiztik

---

### Post by Crafty Kisses on 2009-03-10
First we need a bit more information to start helping you out. Navigate to the Terminal **(Applications->Accessories->Terminal)** and enter the following commands:
```
lspci
lsusb
lshw -C network
ifconfig
iwconfig
```
Copy and paste those one by one, and post the results of each command here on the forum. Then I or someone else can assist you further.

---

### Post by Nicholas.Stacks on 2009-03-10
I am having the same problem on my Serval Professional that I received from System76 today.
The users manual talks about a driver package on a disc, but there was no disc included.

---

### Post by Sadiztik on 2009-03-10
Okay here is the problem with copy and pasteing. Im using my mom's laptop to talk on the forum and my laptop can't connect to the internet. How could i copy and paste onto here?

---

### Post by Nicholas.Stacks on 2009-03-10
Okay... I finally got mine to work.

Whatever drivers I was missing was the problem that caused me to not be able to connect to the wireless -- so I wired the connection, downloaded the 165 updates that were available, restarted and then it should work.

---

### Post by Crafty Kisses on 2009-03-10
I guess if you have a USB drive, you could save the results of those commands in a .txt file and then post the results from the Dell. Alternatively if you can get a wired connection going to your laptop that would be a good way of doing it too.

---

### Post by DeMus on 2009-03-10
> **Sadiztik said:**
> Okay here is the problem with copy and pasteing. Im using my mom's laptop to talk on the forum and my laptop can't connect to the internet. How could i copy and paste onto here?

Type the commands in the terminal and copy (use shift-ctrl-c) and paste the text into a textfile you create with gedit: Applications - Accessories - Text editor.
Then save the file on your desktop or where ever you like and copy it onto a usb stick.

---

### Post by Sadiztik on 2009-03-10
Here ya go. You can see all the commands at the top of each:

sadiztik@Sad-Ubuntu-Lap:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800M GTS (rev a2)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
---------------------------------------------------------------------------------------------------------------------------
sadiztik@Sad-Ubuntu-Lap:~$ lsusb
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway Webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
--------------------------------------------------------------------------------------------------------------------------
sadiztik@Sad-Ubuntu-Lap:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:72:3d:cd:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:44:4a:2f:49:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
-----------------------------------------------------------------------------------------------------------------------------
sadiztik@Sad-Ubuntu-Lap:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:3d:cd:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:217 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50396 (50.3 KB)  TX bytes:50396 (50.3 KB)
---------------------------------------------------------------------------------------------------------------------------
sadiztik@Sad-Ubuntu-Lap:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by Sadiztik on 2009-03-10
Does this information work?

---

### Post by Nicholas.Stacks on 2009-03-10
I can't help you with all of that code stuff... I'm new to Linux; but I just got my wireless to work by wiring the connection, installing the available updates, and restarting my system.  Maybe that will work for you too.

---

### Post by Sadiztik on 2009-03-11
Nah that didn't work. Does anyone know what else I can do? I can't switch back to Vista now so i'm ****** if I don't get help. PLEASE HELP ME :(:(:(:(:(

---

