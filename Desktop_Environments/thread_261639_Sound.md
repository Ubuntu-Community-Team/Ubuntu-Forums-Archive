---
title: "Sound"
date: 2006-09-20
forum: Desktop Environments
---

### Post by robert on 2006-09-20
I tried Ubuntu nearly two years ago but then went over to using Debian itself. However, I've just bought a new computer and Debian did not have a driver for the onboard NIC. Ubuntu has solved that problem but now I cannot get any sound out or should I say normally I can't get any sound.

First I couldn't get any sound at all until I tried:

[http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME)

whereafter I got system sounds at start up sometimes, but XMMS, for example, still would not work at all.

I then went on to play around with the preference settings in XMMS and and added some ALSA software (using Synaptic) that was suggested in a post (now lost in my browser history among the vast number consulted) when just for a few seconds I got some sound. However I went to adjust the sound on the main tray icon, but as soon as I clicked on it I lost the sound again and I've not got it back since.

Really I think I'm "just" asking for the sure-fire way of getting the sound to work.

Command line info:


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8178
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: bdf00000-bfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000eff00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 817f
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at bddf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: bde00000-bdefffff
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 8000 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at 8400 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 8800 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 9000 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 233
        Memory at bddffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 2601
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 225
        I/O ports at a800 [size=8]
        I/O ports at a400 [size=4]
        I/O ports at a000 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9400 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8179
        Flags: medium devsel, IRQ 11
        I/O ports at 0400 [size=32]

0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81aa
        Flags: bus master, fast devsel, latency 0, IRQ 177
        I/O ports at c800 [size=256]
        Memory at bdeff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at bdee0000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:04:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0160 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at bf000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at be000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at bdfe0000 [disabled] [size=128K]
        Capabilities: <available only to root>

$ lsmod|grep snd
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd_hda_intel          18964  5
snd_hda_codec         157616  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  18 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

The sound card, obviously detected, is onboard an ASUS P5LD2 SE mainboard which the manual describes under "High Definition Audio" as:

ADI1986A 6-channel CODEC
Supports jack Sensing and Enumeration Technology
Supports S/PDIF out interface

Any comments or help of any description most appreciated.

Robert

---

### Post by mcmc on 2006-10-01
Try putting the following into a new file inside /etc/modprob.d/ folder (call it sound or something):
"options snd-hda-intel position_fix=1 model=3stack"

(without the quotes)

Then run

Code:

sudo update-modules

and reboot

---

### Post by glantz on 2006-10-18
This worked for me, thank you, however, can anyone explain why this works? I like to know why things work and not just the answer.

---

