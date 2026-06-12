---
title: "no sound after login"
date: 2012-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ecarey on 2012-06-29
Hi All,

I have a fresh install of 12.04 on a DELL M65.  Issue I'm having is once logged in I have no sound output.  Prior to logging in I hear an alert (bongo beat) when the display manager finishes loading and I can toggle the screen reader on and I will hear sound output.  Once I login though I no longer can get sound output.

I have found many old posts for debugging sound issues and have tried most of the steps outlined in them.  One thing I see when running alsamixer is the s/pdif slider is absent but the box under where  the slider should be shows 00.  I can toggle the value to MM from the alsamixer ncurses window or from the speaker menu of the top right Unity menu bar.  Shouldn't there be a slider in the alsamixer control for s/pdif?

output from lspci...

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G72GL [Quadro FX 350M] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

output from aplay -l...
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

What additional info should I post here?

Thanks in advance!

---

### Post by ecarey on 2012-07-01
After more digging I found from another ubuntuforms thread (thank you for this resource :) ) this bit that worked for my use case:

options snd-hda-intel index=0 model=[your model name here] 

to the bottom off /etc/modprobe.d/alsa-base.conf

I found the model name from [http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD) which was a link from this page [http://alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](http://alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA).

For me, the closest match model name was dell-m23.  Dell Precision M65 isn't listed but from alsamixer I saw that my chip set was the STAC9200 and dell-m23 was the only Precision in STAC2900's list.

After making the edit to alsa-base.conf I rebooted.  Checking sound settings then showed a new item in the "Play sound through" list.  The new option was "Analog Output Built-in Audio".  After selecting the new item the test sound worked.

Hope this helps someone.

---

### Post by e23wiz on 2013-05-09
It worked for me Acer Aspire 5100-5033 used model name acer.  thanks!

---

