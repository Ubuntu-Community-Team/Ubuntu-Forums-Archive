---
title: "Sound suddenly doesn't work???"
date: 2008-03-24
forum: Debian
---

### Post by Erwin Criddle on 2008-03-24
Hi, I'm running Debian Lenny.

Suddenly, when I rebooted the computer, sound doesn't work.
I don't know why at all.

Any ideas??   :confused:

---

### Post by deepclutch on 2008-03-26
did u tried a custom kernel?or make sure u unmuted volume control PCM,master etc

---

### Post by D-EJ915 on 2008-03-26
sometimes that happens to me (on my ubuntu system) just reboot again and usually it fixes it...I have no idea what happens but it's such an easy fix I've never bothered to find out, lol.

---

### Post by Erwin Criddle on 2008-03-26
I don't have a custom kernel and I havn't got the sound muted. I have tried rebooting but it doesn't have any effect.

When I try and test sound from System, Preferences, Sound. It says cannot open sound device

---

### Post by deepclutch on 2008-03-26
just check which kernel are installed.u may need to modprobe the modules needed.
check for ur audio h/w by "lspci |grep audio" and also the o/p of "lsmod |grep snd"
and post the o/p here

---

### Post by polmir on 2008-03-26
Type in terminal
```
lspci
```
and post output.

---

### Post by Caraibes on 2008-03-27
You might want to try booting with a live-cd, to make sure sound works, and so you know it is not a hardware-related issue.

---

### Post by Erwin Criddle on 2008-03-28
Output of lspci
```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
02:00.0 USB Controller: NEC Corporation USB (rev 43)
02:00.1 USB Controller: NEC Corporation USB (rev 43)
02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 43)
02:03.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```

Also, when I try booting into the Ubuntu Live CD, the sound works perfectly.

---

### Post by polmir on 2008-03-28
Type in terminal command
```
alsamixer
```
and adjust suitable values of slide control.

---

### Post by Erwin Criddle on 2008-04-21
I tried running 'alsamixer' and adjusted the volume levels. But still no 
sound??

---

### Post by polmir on 2008-04-21
```
 aplay -l
```
please post output of it.

---

### Post by nacnud on 2008-05-19
I'm having this issue too, although I'm using gNewSense (based on Hardy).

Sound worked with the live CD, as well as after install.  But after first update/upgrade and reboot, sound is gone.  I get this message when I try to open the volume control:

"No volume control GStreamer plugins and/or devices found."

aplay -l says "no sound devices found"

Any help would be appreciated!

lspci

```
 lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

```

---

### Post by oaul on 2008-05-22
In case there's an off chance that you compiled with a stock .config for 2.6.24 found in the headers package (theoretically the 'non-custom', default kernel), all sound modules are disabled by default. Definately a mistake there. Happened to me. 

Anyways judging by the sound of your problem (no pun intended) this probably isn't the culprit.

---

### Post by scanman717 on 2008-05-29
I am having this problem.. Happened after I downloaded the kernel headers to get VMWare working in 8.04....  

linux-headers-2.6.24-17-386

Any help appreciated.
Thanks

---

### Post by acl123 on 2008-06-01
I have the exact same problem here on Gutsy. I just turned on the computer this afternoon and my sound is completely gone. None of the suggestions posted on this thread have worked.

Here is my lspci:
> 
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
05:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)


---

### Post by Arthur Archnix on 2008-06-03
This sometimes happens to me when switching operating systems... I find the following fix always works:

1. Power down computer, remove power sources (battery, ac).
2. Hold down power key for 10 seconds, then hit function key + power key for 10 seconds, then (this step is optional) press some more keys and power key for 10 seconds (up to ten keys can be pressed by most people - yours may be less or more depending on genetics / farm accidents).
3. Plug back in and power on without battery. Or with. I don't think it matters.

---

