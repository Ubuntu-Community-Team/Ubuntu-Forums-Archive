---
title: "no sound in the card of radeon for DEll studio 1458"
date: 2010-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vijaydahiya89 on 2010-02-17
hey i have the above mentioned laptop with the  drivers
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevice: 1/1
  Subdevice #0: subdevice #0
I have tried all the below things

1 .root@vijay-laptop:/home/vijay# lspci
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev
12)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root
Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400
Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset
USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset
High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI
Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset
USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC
Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series
Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus
Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility
Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon
HD 4000 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780
Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic
Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System
Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

2. #gedit /etc/modprobe.d/alsa-base.conf
n added
alias   snd-card-0 snd-hda-intel
alias   sound-slot-0 snd-hda-intel
options sndhda-intel model=dell-m6-amic Dell desktops/laptops with
analog mics
options sndhda-intel enable_msi=1
3.#sudo apt - get install gnome-alsamixer



but i did'nt get any sound.....................
Plz help!!!!!!!!!!!!!!!!!!!!!!:lolflag::lolflag::popcorn::popcorn:

---

### Post by azwar on 2010-02-18
Yes, you have exactly the same problem like me. I've Dell Studio 1450, ATI HD Radeon 4530, SRS Surround Realtek (ALC665).

I've got solution by purging alsa and pulse audio from kernel. Please follow the step here [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound").

The sound work great, loud and crystal clear. If the sound to slow just run the command ```
ossxmix
``` then play with the setting until you satisfied with your sound.

---

### Post by vijaydahiya89 on 2010-09-17
:D:o:)
It's working...............
[SIZE=3]
Also it is working in ubuntu 10.10 beta version no need of doing that stuff..............

Anyways thanks a lot bro mazza aa gaya.................
Yuppy..........
[/SIZE]

---

