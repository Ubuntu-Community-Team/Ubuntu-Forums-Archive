---
title: "No sound with onboard 82801 EB (ICH5) - 6 Channel AC97"
date: 2006-06-15
forum: Desktop Environments
---

### Post by pquet on 2006-06-15
What else? I'm having trouble setting up sound. I am attaching the outputs of dmesg, lsmod, lspci -v, cat /proc/interrupts, amixer and cat /proc/devices. Any help would be greatly appreciated!


$ dmesg |grep -e intel8x0 -e ICH5
[4294672.116000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294672.116000] ICH5: chipset revision 2
[4294672.116000] ICH5: not 100% native mode: will probe irqs later
[4294687.343000] intel8x0_measure_ac97_clock: measured 50164 usecs
[4294687.343000] intel8x0: clocking to 48000

$ lsmod |grep snd
snd_cmipci             34336  0
gameport               15496  1 snd_cmipci
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10624  1 snd_cmipci
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_mpu401_uart         7808  1 snd_cmipci
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
snd                    55268  14 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd


$ lspci -v 

0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: ABIT Computer Corp.: Unknown device 100a
        Flags: medium devsel, IRQ 3
        I/O ports at 0500 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: ABIT Computer Corp.: Unknown device 100a
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at d800 [size=256]
        I/O ports at dc00 [size=64]
        Memory at fa101000 (32-bit, non-prefetchable) [size=512]
        Memory at fa102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at a400 [size=256]
        Capabilities: <available only to root>


$ cat /proc/interrupts |grep -e Intel -e CMI
201:       1078   IO-APIC-level  Intel ICH5
209:          0   IO-APIC-level  CMI8738-MC6


$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [on]
  Front Right: Playback 23 [74%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 11 [73%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 11 [73%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [on]
  Front Right: Playback 28 [90%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [on]
  Front Right: Playback 19 [61%] [on]
Simple mixer control 'Surround Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [on]
Simple mixer control 'Center/LFE Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 20 [65%] [on] Capture [on]
  Front Right: Playback 20 [65%] [on] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 2 [67%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 12 [80%] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [on] Capture [off]
  Front Right: Playback 23 [74%] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Analog to IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Swap Surround Slot',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


$ cat /proc/devices |grep -e Character -e sound -e alsa -e Block -e sd
Character devices:
 14 sound
116 alsa
Block devices:
  8 sd
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd

---

### Post by pquet on 2006-06-15
And I did download and install the latest alsa drivers, libraries and utilities 1.0.11, following the instructions given in [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci)

The strange thing is that the sound did work perfectly fine for one single session (not the first one), so i shouldn't be far.

---

