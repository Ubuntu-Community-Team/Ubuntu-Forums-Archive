---
title: "Dell Studio 15 Dual Headphones"
date: 2010-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rhinofloyd on 2010-11-14
Hi everyone.

I am running Ubuntu 10.10 on a new Dell Studio 15. It has 2 headphone sockets but only one appears to be working.

Any ideas on how to fix this? Also, is there anyway to make one of them a monitor (for dj'ing) and one the master out?

Guidance on this matter would be greatly appreciated.

---

### Post by Hakachukai on 2011-01-19
I have a Dell Studio 1745 with Dual headphones jacks, but neither one of them work :-(

As soon as I plug in my head set, it turns off the speakers but I get no sound out of the jack.

Speakers work, Mic input works... just not the headphone jacks.

How do I fix this? I take it that days of the speaker wires simply being physically connected to the headphones are gone :-(

It's not the head set BTW. I use it everyday, I know it works.

---

### Post by Hakachukai on 2011-01-19
I have a Dell Studio 1745 with Dual headphones jacks, but neither one of them work :-(

As soon as I plug in my head set, it turns off the speakers but I get no sound out of the jack.

Speakers work, Mic input works... just not the headphone jacks.

How do I fix this? I take it that days of the speaker wires simply being physically connected to the headphones are gone :-(

It's not the head set BTW. I use it everyday, I know it works.

----------------------------------------------------------------------------

user@machine:~$ lspci
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

--------------------------------------------------------------------------

user@machine:~$ lsmod 
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  30022  1 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54887  1 
joydev                  8735  0 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
i915                  290938  3 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
drm_kms_helper         30200  1 i915
iwlagn                178948  0 
drm                   168054  4 i915,drm_kms_helper
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
iwlcore               127415  1 iwlagn
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  2 iwlagn,iwlcore
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
dell_laptop             5730  0 
cfg80211              144470  3 iwlagn,iwlcore,mac80211
dell_wmi                2852  0 
dcdbas                  5402  1 dell_laptop
intel_agp              26360  2 i915
videodev               43098  1 uvcvideo
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
r8169                  36489  0 
libahci                21667  4 ahci
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 r8169

---

### Post by Hakachukai on 2011-01-19
sorry, some how I submitted a duplicate post :-(

---

### Post by Hakachukai on 2011-01-19
sorry, some how I submitted a duplicate post :-(

---

### Post by Hakachukai on 2011-01-19
sorry, some how I submitted a duplicate post :-(

---

### Post by Hakachukai on 2011-02-05
This fixed my issues:

I added this line to the end of /etc/modprobe.d/alsa-base.conf

--------------------------------------

options snd-hda-intel model=dell-m6

--------------------------------------

I got that value according to my laptop model from this page:
[http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)

---

