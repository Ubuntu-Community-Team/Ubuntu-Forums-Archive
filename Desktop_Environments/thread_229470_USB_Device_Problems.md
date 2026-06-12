---
title: "USB Device Problems"
date: 2006-08-04
forum: Desktop Environments
---

### Post by paradj on 2006-08-04
eMachine T1360
Intel Celeron-S, 1300 MHz CPU
Intel Whitney i810E Chipset
Trigem Lomita Motherboard
Phoenix BIOS
2 x 128 MB SDRAM (reported as 253MB)
Intel(R) 82810E Integrated Graphics Controller (4 MB) 
Intel i752 3D Accelerator 
Intel(r) 82801AA Bus Master IDE Controller
Intel 82801AA I/O Controller Hub - AC'97 Audio Adapter
Intel 82801AA I/O Controller Hub - USB Controller
(standard T1360 eMachine)
ubuntu 6.06LTS (with recent ubuntu-automated updates)



Problem 
working HP Deskjet 832c USB printer is reported as
 ProductID: Unknown 0x7148 
 usb.device.vendor: eSOL Co., Ltd

have tried setting up manually using installed hplip v.097???
no device detected.

set to CUPS ipp id as suggested by HP:
 "ipp://hp://" 
-my understanding is that something is wrong with this uri.
-this don't work either

tried to update with the hplip driver from HP
seems that the needed compilers are not found installed nor in the synaptic package manager??? 

my research points to this reported device from "eSOL Co., Ltd" as 
an integrated Windows Media Digital Rights Management device?

so how does one replace an incorrect "device driver" in ubuntu/linux?

what the heck is this? 

also the the right-click-context-window-control on mouse seems to pop-up all by itself....a mind of its own...
tried replacing with new mouse(original Dell USB MSWheelMouse, Replacement First/Pilot USB WheelMouse) will try std ps/2 later as i believe this to be a USB Device error also.

this system works perfectly with Windows 2000 sp4, Windows 2003 server, and Windows XP SP2, and with the "Breezy Badger" release v5.10

realize that above mentioned os's are installed via OEMCD's(eg. Microsoft, Canonical) on seperate drives not upgraded(excluding win2ksp4)

---

### Post by paradj on 2006-08-04
ok so this seems to be a USB device identification problem

replaced USB mouse with std ps/2 MS WheelMouse - no mind-of-its-own-context menus popping up anywhere/everywhere

also gotta wonder how secure is this OS?

anyone getting a flying duck in the smilies for a "boohoo"?

see attached image:
ubuntuforum-whatsthis.png

---

### Post by paradj on 2006-08-04
mind-of-its-own-context menu now only appears when i use the top row (numbers and symbols) of the USB 2 Port Multi-Media Keyboard


here's what lspci outputs:

0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:0e.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)


-----
pm me for any futher info if needed

also a note to those who know...
the device data base could use a bit more enduser input(what works what don't etc) and the ability to correct any malformed submissions by addendum
so devs could see in realworld app how systems are seen on install...


---
still see the damned duck....>>

---

### Post by paradj on 2006-09-12
#-o 
ok so i "fixed" this by trading that Dell USB Keyboard with a standard PS/2 style one.

Now, that keyboard seems to be working fine on the Dual-Boot W2k/XP-Based PC; and this one hasn't had any probs with the standard keyboard.

NOTE: this may have been an hardware incompatiblity prob with the Dell MultiMedia (or any?)USB Keyboards and the EMachines(Trigem Lomita based) ACPI USB Controller as an XP install did the same thing..:confused:

---

