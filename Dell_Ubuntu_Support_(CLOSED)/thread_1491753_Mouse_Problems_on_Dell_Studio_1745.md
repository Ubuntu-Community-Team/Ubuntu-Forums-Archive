---
title: "Mouse Problems on Dell Studio 1745"
date: 2010-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by streed on 2010-05-24
Okay, so I just installed 10.04 on my laptop and whenever I put two fingers on the mouse touch-pad, the cursor goes berserk and flies all over the screen. It gets extremely annoying and it'd be appreciated if someone could help me fix it. :)

Also, how can I enable the two-finger scrolling on this laptop? It won't let me. :(

---

### Post by freesitebuilder on 2010-06-29
Have you solved this? I've tried the LiveCD of 10.04 and have the same problem.

I've now tried with a USB mouse, and it works fine - touching the touchpad seems to cause problems.

---

### Post by Hakachukai on 2011-01-11
I have a similar issue.

Dell Studio 1745, Ubuntu 10.10

The mouse pad is totally dead. It didn't work with the Desktop CD or after the installation. I'm currently having to use a USB mouse

--------------------------------------------------------------------------

root@laptop:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Network controller: Intel Corporation WiFi Link 5100
14:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
14:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
14:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
20:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
root@laptop:~# 

--------------------------------------------------------------------------

root@laptop:~# lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:6406 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

--------------------------------------------------------------------------

root@laptop:~# lsmod
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  30022  1 
usbhid                 36882  0 
hid                    67742  1 usbhid
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  2 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54887  1 
iwlagn                178948  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
iwlcore               127415  1 iwlagn
i915                  290938  4 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30200  1 i915
drm                   168054  5 i915,drm_kms_helper
mac80211              231541  2 iwlagn,iwlcore
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
intel_agp              26360  2 i915
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144470  3 iwlagn,iwlcore,mac80211
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  1 i915
lp                      7342  0 
dell_laptop             5730  0 
output                  1883  1 video
dcdbas                  5402  1 dell_laptop
dell_wmi                2852  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
ahci                   19013  0 
r8169                  36489  0 
led_class               2633  1 sdhci
libahci                21667  4 ahci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 r8169
root@laptop:~# 

--------------------------------------------------------------------------

---

### Post by Hakachukai on 2011-01-11
I should add that this:

Bus 006 Device 005: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 

Is the external USB mouse that I plugged in

---

### Post by Hakachukai on 2011-01-12
So, I rebooted to dual boot another OS and when I booted Ubuntu 10.10 the 2nd time the mouse pad went crazy one time, then started working normally.

I'm not complaining... but... ???

---

### Post by Hakachukai on 2011-04-06
Here is an update on an old issue, that still haunts me

I noticed that if the mouse doesn't work, I have to both remove my SD memory card from the card slot AND unplug my laptop power supply before Ubuntu boots up.

If I do these 2 things the mouse pad will work in Ubuntu. If I don't, it remains completely dead

---

