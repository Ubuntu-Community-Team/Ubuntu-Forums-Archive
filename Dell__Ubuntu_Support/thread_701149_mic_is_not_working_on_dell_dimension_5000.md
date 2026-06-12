---
title: "mic is not working on dell dimension 5000"
date: 2008-02-19
forum: Dell  Ubuntu Support
---

### Post by danbyte on 2008-02-19
Hi all,

I own a dell dimension 5000 desktop and I've been trying to configure my mic in order to use programs like skype but no luck. I'm running Ubuntu 7.10 Gutsy Gibbon.

I hear sounds fine but my mic is not working (I use arecord to test it and all I hear is silence). Below some hardware details:

daniel@daniel-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
04:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:03.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

When I do "arecord -d 10 -f S16_LE -r 48000 -c 2 -t wav foobar.wav" and I literally put one of the speaker at full volume in one of my ears I can hear a very vere low volume version of myself.

Here's my amixer settings (I use alsamixer -c 0 to configure any changes)

daniel@daniel-desktop:~$ amixer -c 0 
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 26 [84%] [4.50dB] [on] Capture [on]
  Front Right: Playback 26 [84%] [4.50dB] [on] Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic2'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 14 [93%] [21.00dB] [on]
  Front Right: Capture 14 [93%] [21.00dB] [on]
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
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Downmix',0
  Capabilities: enum
  Items: 'Off' '6 -> 4' '6 -> 2'
  Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Mic/Line In',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
  Capabilities: enum
  Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
  Item0: '3.7 V'


This is the only thing that's stopping me from doing a full migration from windows (mic works ok here) to linux at home (all right, I'll have to sort out the webcam as well but I asked my wife for some credit here)

Any comments that could help me to boost my mic volume are highly appreciated.

Thanks in advance,

Daniel

---

### Post by oni5115 on 2008-02-19
Make sure the mic boost is checked.  The value you display is 0, I assume that is false/ off and that 1 would be true/on.

I'm quite interested in seeing what happens though, my XPS m170 seems to have the same sound card so maybe if you can get it working I can as well.

---

### Post by danbyte on 2008-02-19
Thanks for your reply Oni,

The only thing that changes when change the mic boost setting using alsamixer is the mono playback from off to on ...

Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
 [COLOR="Red"] Mono: Playback [on][/COLOR]

I don't think the digit zero is a boolean value for any of the settings. Can you confirm if it changes on your system when you mute/unmute the parameter in your system?

Cheers,

Dan

---

### Post by danbyte on 2008-02-19
Hi all,

I own a dell dimension 5000 desktop and I've been trying to configure my mic in order to use programs like skype but no luck. I'm running Ubuntu 7.10 Gutsy Gibbon.

I hear sounds fine but my mic is not working (I use arecord to test it and all I hear is silence). Below some hardware details:

daniel@daniel-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
04:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:03.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

When I do "arecord -d 10 -f S16_LE -r 48000 -c 2 -t wav foobar.wav" and I literally put one of the speaker at full volume in one of my ears I can hear a very vere low volume version of myself.

Here's my amixer settings (I use alsamixer -c 0 to configure any changes)

daniel@daniel-desktop:~$ amixer -c 0
Simple mixer control 'Master',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 25 [81%] [-9.00dB] [on]
Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Mono',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 22 [71%] [-13.50dB] [on]
Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Headphone Jack Sense',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'PCM',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 25 [81%] [3.00dB] [on]
Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Surround',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 0 [0%] [-46.50dB] [off]
Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Jack Mode',0
Capabilities: enum
Items: 'Shared' 'Independent'
Item0: 'Shared'
Simple mixer control 'Center',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'CD',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 26 [84%] [4.50dB] [on] Capture [on]
Front Right: Playback 26 [84%] [4.50dB] [on] Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Mic Select',0
Capabilities: enum
Items: 'Mic1' 'Mic2'
Item0: 'Mic2'
Simple mixer control 'Video',0
Capabilities: cswitch cswitch-exclusive
Capture exclusive group: 0
Capture channels: Front Left - Front Right
Front Left: Capture [off]
Front Right: Capture [off]
Simple mixer control 'Phone',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Mono
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono: Playback 0 [0%] [-34.50dB] [off]
Front Left: Capture [off]
Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 15
Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
Capabilities: enum
Items: 'Mix' 'Mic'
Item0: 'Mix'
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 14 [93%] [21.00dB] [on]
Front Right: Capture 14 [93%] [21.00dB] [on]
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
Simple mixer control 'Channel Mode',0
Capabilities: enum
Items: '2ch' '4ch' '6ch'
Item0: '2ch'
Simple mixer control 'Downmix',0
Capabilities: enum
Items: 'Off' '6 -> 4' '6 -> 2'
Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Exchange Mic/Line In',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'External Amplifier',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
Capabilities: enum
Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
Item0: '3.7 V'


This is the only thing that's stopping me from doing a full migration from windows (mic works ok here) to linux at home (all right, I'll have to sort out the webcam as well but I asked my wife for some credit here)

Any comments that could help me to boost my mic volume are highly appreciated.

Thanks in advance,

Daniel

---

### Post by danbyte on 2008-02-19
Hi all,

I own a dell dimension 5000 desktop and I've been trying to configure my mic in order to use programs like skype but no luck. I'm running Ubuntu 7.10 Gutsy Gibbon.

I hear sounds fine but my mic is not working (I use arecord to test it and all I hear is silence). Below some hardware details:

daniel@daniel-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
04:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:03.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

When I do "arecord -d 10 -f S16_LE -r 48000 -c 2 -t wav foobar.wav" and I literally put one of the speaker at full volume in one of my ears I can hear a very vere low volume version of myself.

Here's my amixer settings (I use alsamixer -c 0 to configure any changes)

daniel@daniel-desktop:~$ amixer -c 0
Simple mixer control 'Master',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 25 [81%] [-9.00dB] [on]
Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Mono',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 22 [71%] [-13.50dB] [on]
Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Headphone Jack Sense',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'PCM',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 25 [81%] [3.00dB] [on]
Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Surround',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 0 [0%] [-46.50dB] [off]
Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Jack Mode',0
Capabilities: enum
Items: 'Shared' 'Independent'
Item0: 'Shared'
Simple mixer control 'Center',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'CD',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 26 [84%] [4.50dB] [on] Capture [on]
Front Right: Playback 26 [84%] [4.50dB] [on] Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Mic Select',0
Capabilities: enum
Items: 'Mic1' 'Mic2'
Item0: 'Mic2'
Simple mixer control 'Video',0
Capabilities: cswitch cswitch-exclusive
Capture exclusive group: 0
Capture channels: Front Left - Front Right
Front Left: Capture [off]
Front Right: Capture [off]
Simple mixer control 'Phone',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Mono
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono: Playback 0 [0%] [-34.50dB] [off]
Front Left: Capture [off]
Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 15
Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
Capabilities: enum
Items: 'Mix' 'Mic'
Item0: 'Mix'
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 14 [93%] [21.00dB] [on]
Front Right: Capture 14 [93%] [21.00dB] [on]
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
Simple mixer control 'Channel Mode',0
Capabilities: enum
Items: '2ch' '4ch' '6ch'
Item0: '2ch'
Simple mixer control 'Downmix',0
Capabilities: enum
Items: 'Off' '6 -> 4' '6 -> 2'
Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Exchange Mic/Line In',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'External Amplifier',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
Capabilities: enum
Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
Item0: '3.7 V'


This is the only thing that's stopping me from doing a full migration from windows (mic works ok here) to linux at home (all right, I'll have to sort out the webcam as well but I asked my wife for some credit here)

Any comments that could help me to boost my mic volume are highly appreciated.

Thanks in advance,

Daniel

---

### Post by danbyte on 2008-02-19
Hi all,

I own a dell dimension 5000 desktop and I've been trying to configure my mic in order to use programs like skype but no luck. I'm running Ubuntu 7.10 Gutsy Gibbon.

I hear sounds fine but my mic is not working (I use arecord to test it and all I hear is silence). Below some hardware details:

daniel@daniel-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
04:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:03.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

When I do "arecord -d 10 -f S16_LE -r 48000 -c 2 -t wav foobar.wav" and I literally put one of the speaker at full volume in one of my ears I can hear a very vere low volume version of myself.

Here's my amixer settings (I use alsamixer -c 0 to configure any changes)

daniel@daniel-desktop:~$ amixer -c 0
Simple mixer control 'Master',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 25 [81%] [-9.00dB] [on]
Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Master Mono',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 22 [71%] [-13.50dB] [on]
Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'Headphone Jack Sense',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'PCM',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 25 [81%] [3.00dB] [on]
Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Surround',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 0 [0%] [-46.50dB] [off]
Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Jack Mode',0
Capabilities: enum
Items: 'Shared' 'Independent'
Item0: 'Shared'
Simple mixer control 'Center',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'CD',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 26 [84%] [4.50dB] [on] Capture [on]
Front Right: Playback 26 [84%] [4.50dB] [on] Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Mic Select',0
Capabilities: enum
Items: 'Mic1' 'Mic2'
Item0: 'Mic2'
Simple mixer control 'Video',0
Capabilities: cswitch cswitch-exclusive
Capture exclusive group: 0
Capture channels: Front Left - Front Right
Front Left: Capture [off]
Front Right: Capture [off]
Simple mixer control 'Phone',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Mono
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono: Playback 0 [0%] [-34.50dB] [off]
Front Left: Capture [off]
Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 15
Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
Capabilities: pvolume pswitch cswitch cswitch-exclusive
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: Playback 0 - 31
Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
Capabilities: enum
Items: 'Mix' 'Mic'
Item0: 'Mix'
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 14 [93%] [21.00dB] [on]
Front Right: Capture 14 [93%] [21.00dB] [on]
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
Simple mixer control 'Channel Mode',0
Capabilities: enum
Items: '2ch' '4ch' '6ch'
Item0: '2ch'
Simple mixer control 'Downmix',0
Capabilities: enum
Items: 'Off' '6 -> 4' '6 -> 2'
Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Exchange Mic/Line In',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'External Amplifier',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
Capabilities: enum
Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
Item0: '3.7 V'


This is the only thing that's stopping me from doing a full migration from windows (mic works ok here) to linux at home (all right, I'll have to sort out the webcam as well but I asked my wife for some credit here)

Any comments that could help me to boost my mic volume are highly appreciated.

Thanks in advance,

Daniel

---

### Post by oni5115 on 2008-02-19
I can try, not sure where to get these values from, or what command to run. 

I did finally get mine working using the Gnome Volume Control 1.20.1, and playing around with the "Capture" option.  Apparently, I even though I had microphone on and unmuted, I had missed this and it was failing to capture because it was muted or turned down really low.

Unfotunately, I then got stupid and decided to try out Pulse Audio, so I don't know if it still works or not... the only thing I needed the mic for was Ventrilo, and unfortunately, Pulse Audio seems to hate Wine 9.54.  (Waiting to see if someone can post compiling instructions in another thread so I can try and get a new version of PA that might work with Wine.)

Anyways, just let me know what commands to run to get those values for you, and I can try and post what I have.

---

### Post by danbyte on 2008-02-20
Hi Oni,

can you try amixer -c 0 adn post the results?

Cheers,

Daniel

---

### Post by oni5115 on 2008-02-20
Certainly can do:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 14 [45%] [-25.50dB] [on]
  Front Right: Playback 14 [45%] [-25.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 14 [45%] [-25.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-12.00dB] [on]
  Front Right: Playback 15 [48%] [-12.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 13 [42%] [-15.00dB] [off] Capture [off]
  Front Right: Playback 13 [42%] [-15.00dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 17 [55%] [-9.00dB] [on] Capture [off]
  Front Right: Playback 17 [55%] [-9.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
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
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 5 [33%] [-30.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 6 [40%] [9.00dB] [on]
  Front Right: Capture 6 [40%] [9.00dB] [on]
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
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

Also, got it working in wine as well.  Despite my error messages, I just needed to switch it to ESD instead of ALSA.  Being able to have different volume levels for Audacious / Ventrilo ftw!

---

### Post by danbyte on 2008-02-23
Thanks oni,

one of the key differences I see here are the capabilities for our mics

Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive

Are you using the built in mic or an external one?

Do you know what alsa version you're using ? Can you post the contents  of /etc/modprobe.conf and ~/.asoundrc?

Dan

---

### Post by oni5115 on 2008-02-23
Using the default mic jack of my XPS m170.  The actual microphone is from my headset.

I don't have either of those files.  I do however, have:/etc/asound.conf

However, it is simply setup for Pulse Audio at the moment. I believe I had to create the file too, when I setup PulseAudio, so there wouldn't have been anything in there from before.

alsa-base - 1.0.14-1ubuntu2
alsa-utils - 1.0.14-1ubuntu4

---

