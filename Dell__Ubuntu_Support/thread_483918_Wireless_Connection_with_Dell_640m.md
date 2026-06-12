---
title: "Wireless Connection with Dell 640m"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by phoenix7 on 2007-06-25
Is there anyone who know how to use wireless connection in ubuntu 7.04 with Dell 640m?

my lspci output is as follows:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
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
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by sj3fk3 on 2007-07-04
> **phoenix7 said:**
> Is there anyone who know how to use wireless connection in ubuntu 7.04 with Dell 640m?

my lspci output is as follows:

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Nothing wrong with that as far as I can see, have you installed network-manager-gnome? 'sudo apt-get install network-manager-gnome'? 
What output does iwconfig give you?

---

### Post by phoenix7 on 2007-07-09
The result of iwconfig is:

lo        no wireless extensions.
eth0      no wireless extensions.

I don't how to turn on the wireless device! The associated key is FN-F2 in Microsoft Windows, but it does not work in linux! Does anyone know how to turn on the wireless device?

--
Thanks,

---

### Post by sj3fk3 on 2007-07-09
> **phoenix7 said:**
> The result of iwconfig is:

lo        no wireless extensions.
eth0      no wireless extensions.

I don't how to turn on the wireless device! The associated key is FN-F2 in Microsoft Windows, but it does not work in linux! Does anyone know how to turn on the wireless device?

--
Thanks,

Normally you do not need to turn it on with any key combination. Using Gnome network manager helps setting up a wireless connection.

---

### Post by phoenix7 on 2007-07-09
I'm using KDE!

---

### Post by sj3fk3 on 2007-07-09
> **phoenix7 said:**
> I'm using KDE!

I DIDN'T KNOW THAT!

---

### Post by cyberjames on 2007-07-21
phoenix7:

I think this thread is related to your problem. [**Check this out**]("http://ubuntuforums.org/showthread.php?t=386292&highlight=640m")

-cyberjames-

> 
Quote:
Originally Posted by phoenix7 View Post
I'm using KDE!
I DIDN'T KNOW THAT!

---

