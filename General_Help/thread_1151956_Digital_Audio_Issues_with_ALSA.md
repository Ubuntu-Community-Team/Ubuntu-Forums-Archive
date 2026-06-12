---
title: "Digital Audio Issues with ALSA"
date: 2009-05-07
forum: General Help
---

### Post by KillerSiafu on 2009-05-07
I'm running Jaunty on my desktop PC which I'm configuring as a media center using xbmc. I've configured xbmc and alsamixer to output sound through iec958.

However, I'm not getting any sound coming from certain media types. The standard analog output seems to be working as I can play mp3's and I hear the output fine from standard divx movies etc...

When I switch to viewing HD content that uses digital out, I can't hear anything... This happens in xbmc as well as mplayer.

I followed the instructions on this page for installing the ALSA sound drivers:

[http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step#Upgrading_ALSA_.28sound_driver.29_to_the_latest_version](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step#Upgrading_ALSA_.28sound_driver.29_to_the_latest_version)

Here is some additional info:

```

$ asoundconf list
Names of available sound cards:
NVidia


$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfc100000 irq 21


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ lsmod | grep snd
snd_hda_codec_realtek   199428  1 
snd_hda_intel          33608  8 
snd_hda_codec          76800  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            39296  0 
snd_seq_midi           14240  0 
snd_rawmidi            29472  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29320  3 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66724  27 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

```

```

$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.19 emulation code)
Kernel: Linux mediabox 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA NVidia at 0xfc100000 irq 21

Audio devices:
0: ALC888 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC888

```

```

$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a3)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:04.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:05.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:05.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:05.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:06.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:06.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:08.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8500 GT [10de:0421] (rev a1)

```

---

