---
title: "No sound output in 16.04"
date: 2016-05-01
forum: Desktop Environments
---

### Post by Gridwalker on 2016-05-01
I have lost all sound in Ubuntu 16.04 and I cannot work out why. Pulse Audio Mixer clearly shows that it is detecting an audio stream, and the audio was working only yesterday. My cables, speakers and volume levels are all fine. I have tested all of the output jacks using headphones, reinstalled Pulse Audio, pavucontrol & ALSA, and followed numerous guides that I have found online, all with no success. 

I don't want to use 5.1 surround or optical output - I just want to use a single 3.5mm jack, but checking sound output devices in the settings app only shows S/PDIF Digital output as an option. I have tried testing the audio using 15.04 & 15.10 live CDs without success (16.04 live won't boot at all), but this should be irrelevant because the sound was working yesterday!

**aplay -l** returns :
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 

**lspci -v** returns :
```
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: ASUSTeK Computer Inc. SBx00 Azalia (Intel HDA)
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f7600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

```


I have gone through the following guides : 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[http://askubuntu.com/questions/613370/no-audio-after-updating-to-15-04]("http://askubuntu.com/questions/613370/no-audio-after-updating-to-15-04")


None of the steps were successful.

**bash alsa-info.sh --stdout** returns :
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun May  1 14:21:25 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 16.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      To be filled by O.E.M.
Product Name:      To be filled by O.E.M.
Product Version:   To be filled by O.E.M.
Firmware Version:  2501


!!Kernel Information
!!------------------

Kernel release:    4.4.0-21-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.4.0-21-generic
Library version:    1.1.0
Utilities version:  1.1.0


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf7600000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1043:84fb


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC892
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0892
Subsystem Id: 0x104384fb
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=5, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x2e 0x2e]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC892 Alt Analog", type="Audio", device=2
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0xae 0xae]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f] [0x9f 0x9f] [0x9f 0x9f] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=07, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=08, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Line Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4007e629: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = White
    DefAssociation = 0x2, Sequence = 0x9
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 May  1 15:04 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  7 May  1 15:04 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  4 May  1 15:05 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 May  1 15:05 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 May  1 15:08 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  6 May  1 15:04 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  1 May  1 15:04 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May  1 15:04 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  1 15:04 .
drwxr-xr-x 3 root root 220 May  1 15:04 ..
lrwxrwxrwx 1 root root  12 May  1 15:04 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC892 Alt Analog [ALC892 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf7600000 irq 16'
  Mixer name	: 'Realtek ALC892'
  Components	: 'HDA:10ec0892,104384fb,00100302'
  Controls      : 51
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [on]
  Front Right: Capture 46 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [off]
  Front Right: Capture 46 [100%] [30.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.SB {
	control.1 {
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Center Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.6 {
		iface MIXER
		name 'LFE Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.7 {
		iface MIXER
		name 'Center Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'Side Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.10 {
		iface MIXER
		name 'Side Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.11 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 -6400
			dbvalue.1 -6400
		}
	}
	control.12 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.13 {
		iface MIXER
		name 'Loopback Mixing'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.14 {
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.15 {
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.16 {
		iface MIXER
		name 'Rear Mic Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.17 {
		iface MIXER
		name 'Rear Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.18 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 31
		value.1 31
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.19 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.20 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.21 {
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.22 {
		iface MIXER
		name 'Input Source'
		index 1
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.23 {
		iface MIXER
		name 'Capture Volume'
		value.0 46
		value.1 46
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 46'
			dbmin -1600
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
	control.24 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.25 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 46
		value.1 46
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 46'
			dbmin -1600
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
	control.26 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.27 {
		iface MIXER
		name 'Front Mic Boost Volume'
		value.0 3
		value.1 3
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
	control.28 {
		iface MIXER
		name 'Rear Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.29 {
		iface MIXER
		name 'Line Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.30 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.31 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface MIXER
		name 'Master Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.36 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.37 {
		iface CARD
		name 'Front Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.38 {
		iface CARD
		name 'Rear Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.39 {
		iface CARD
		name 'Line Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.40 {
		iface CARD
		name 'Line Out Front Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.41 {
		iface CARD
		name 'Line Out Surround Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.42 {
		iface CARD
		name 'Line Out CLFE Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.43 {
		iface CARD
		name 'Line Out Side Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.44 {
		iface CARD
		name 'Front Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.45 {
		iface CARD
		name 'SPDIF Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.46 {
		iface CARD
		name 'SPDIF Phantom Jack'
		index 1
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.47 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access read
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.48 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.49 {
		iface PCM
		device 1
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.50 {
		iface PCM
		device 2
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.51 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
xt_tcpudp
iptable_filter
ip_tables
x_tables
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
rfcomm
bnep
binfmt_misc
zfs
zunicode
zcommon
znvpair
spl
zavl
nvidia
snd_hda_codec_realtek
snd_hda_codec_generic
btusb
snd_hda_intel
btrtl
btbcm
snd_hda_codec
btintel
input_leds
joydev
kvm_amd
bluetooth
kvm
snd_hda_core
snd_hwdep
snd_pcm
irqbypass
crct10dif_pclmul
crc32_pclmul
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
aesni_intel
snd_seq
eeepc_wmi
asus_wmi
aes_x86_64
sparse_keymap
lrw
video
gf128mul
glue_helper
mxm_wmi
snd_seq_device
snd_timer
fam15h_power
ablk_helper
edac_mce_amd
snd
cryptd
edac_core
k10temp
serio_raw
soundcore
i2c_piix4
drm
tpm_infineon
shpchp
8250_fintek
mac_hid
wmi
parport_pc
ppdev
lp
parport
autofs4
raid10
raid456
async_raid6_recov
async_memcpy
async_pq
async_xor
async_tx
xor
raid6_pq
libcrc32c
raid1
raid0
multipath
linear
hid_generic
usbhid
hid
psmouse
ahci
r8169
libahci
mii
fjes


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x99430140
0x12 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19850
0x19 0x02a19c60
0x1a 0x0181305f
0x1b 0x02214c20
0x1c 0x411111f0
0x1d 0x4007e629
0x1e 0x01456130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

```

Any thoughts?

---

### Post by Gridwalker on 2016-05-01
Interestingly, I have found another person with the same motherboard reporting similar symptoms on a windows build : [http://www.tomshardware.co.uk/answers/id-1781146/asus-m5a99fx-pro-realtek-sound-problem.html](http://www.tomshardware.co.uk/answers/id-1781146/asus-m5a99fx-pro-realtek-sound-problem.html)

The eventual solution was down to driver certification, so I don't know how useful that is ...

---

### Post by Gridwalker on 2016-05-01
Bios updated ... no luck

---

### Post by Gridwalker on 2016-05-12
Bump ... anybody?

---

### Post by QIII on 2016-05-12
Hello!

Please don't wait so long to bump your post.  It was surely buried pretty deep.

We consider about 12 hours without a response to be a reasonable time to wait before bumping.  That will get you some visibility on the other side of the globe.

Cheers!

---

### Post by Gridwalker on 2016-05-12
Sorry ... I had some new components on order, so I figured I'd wait until I'd completed my rebuild before coming back to the problem.

I will bare this in mind for the future.

---

### Post by CharlesT423 on 2016-05-14
What is the model of motherboard you are using?  Also, can you include the output of "sudo lspci"? Oh, and are you using the 3.55mm jack on the front of the PC or the back?  If you are using the front I'd recommend trying the back (and vice versa as a test) and make sure your speakers/headphones are plugged into the lime green coloured jack and not the block or pink ones.

---

### Post by shantiq on 2016-08-08
do not where you got to but sometimes the default setting on a new install or upgrade do not go to where you need

so install pavucontrol    ```
sudo apt install pavucontrol
```

 and click on configuration

The default here was Analog Stereo Duplex 
         
For me it meant zero sound

Changed it to surround further down the list and voila
So try that
Oe whoever reads this thread with same very annoying drawback


see pics for help 
  
[ATTACH=CONFIG]270652[/ATTACH][ATTACH=CONFIG]270653[/ATTACH]

---

### Post by krishnachaitu on 2016-08-08
friends,i solved the problem of no sound after update to ubuntu 16
you just open alsamixer in terminal and unmute line by typing m you set the automute disabled and loopback disabled
this loopback is the culprit it prevents sound to play through output

---

### Post by al-thomason on 2016-12-24
> **krishnachaitu said:**
> friends,i solved the problem of no sound after update to ubuntu 16
you just open alsamixer in terminal and unmute line by typing m you set the automute disabled and loopback disabled
this loopback is the culprit it prevents sound to play through output

After HOURS spent looking for the soluton, this was it.  THANKS.   No idea why outputs were Muted, but they were and this solved it.

---

