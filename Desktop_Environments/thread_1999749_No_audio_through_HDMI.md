---
title: "No audio through HDMI"
date: 2012-06-08
forum: Desktop Environments
---

### Post by Mrcleanandfresh on 2012-06-08
I have about 10 years IT experience, but have never worked with linux or ubuntu. Thought I would try something new, but it's like starting all over again knowing nothing. This is the first time I have ever asked for help online, so be gentle.

I just built a HTPC with ECS A75F-M FM1 motherboard and AMD A6-3650 Llano 2.6GHz processor. Using the on board HDMI, I am able to see video just fine. No problems, no speed issues. However, there is no audio through HDMI. Under audio devices is shows the two analog audio outputs, but no HDMI audio source.

Normally I would check for drivers... but since I have no idea what I am doing, and there are no linux/ubuntu specific drivers from the manufacture, I am turning to the community for help before I install the windows 8 preview instead. I have already read through 2 dozen similar threads and either they haven't worked, they don't quite apply to my situation, or the explanations were so vague I wasn't able to follow.

---

### Post by Gromit83 on 2012-06-20
I have exactly the same problem. Installed the Radeon driver from AMD and no go.

Just built with a A75 chipset.

I'm using a Gigabyte A75M-S2V with the A8-3870k.

---

### Post by steeldriver on 2012-06-20
iirc on my A8 / ASUS FA75-M Pro box with mythbuntu 11.10 I got no HDMI sound output with either the default radeon driver OR the version of fglrx from 'Additional drivers' - however the later version(s?) from the ATI/AMD website worked (except for flashplayer - which required an extra step of setting a default pulseaudio device)

it was very frustrating because all the usual tests with aplay showed it was working

I assume you've gone through all the usual steps - making sure it's unmuted in alsamixer and so on?

---

### Post by Gromit83 on 2012-06-20
Nope. Not even seeing it at all

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
cat /proc/asound/devices 

  1:        : sequencer
  2: [ 0- 2]: digital audio capture
  3: [ 0- 1]: digital audio playback
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 0]: hardware dependent
  7: [ 0]   : control
 33:        : timer
```

```
cat /proc/modules
 
rfcomm 47946 0 - Live 0x0000000000000000
bnep 18436 2 - Live 0x0000000000000000
bluetooth 166150 10 rfcomm,bnep, Live 0x0000000000000000
parport_pc 36962 0 - Live 0x0000000000000000
ppdev 17113 0 - Live 0x0000000000000000
binfmt_misc 17540 1 - Live 0x0000000000000000
vesafb 13844 1 - Live 0x0000000000000000
snd_hda_codec_realtek 330815 1 - Live 0x0000000000000000
snd_hda_intel 33390 2 - Live 0x0000000000000000
snd_hda_codec 104968 2 snd_hda_codec_realtek,snd_hda_intel, Live 0x0000000000000000
snd_hwdep 13668 1 snd_hda_codec, Live 0x0000000000000000
snd_pcm 96714 2 snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
snd_seq_midi 13324 0 - Live 0x0000000000000000
snd_rawmidi 30547 1 snd_seq_midi, Live 0x0000000000000000
snd_seq_midi_event 14899 1 snd_seq_midi, Live 0x0000000000000000
snd_seq 61896 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
snd_timer 29991 2 snd_pcm,snd_seq, Live 0x0000000000000000
snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
joydev 17693 0 - Live 0x0000000000000000
snd 68266 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x0000000000000000
fglrx 3101156 75 - Live 0x0000000000000000 (P)
soundcore 12680 1 snd, Live 0x0000000000000000
i2c_piix4 13301 0 - Live 0x0000000000000000
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm, Live 0x0000000000000000
serio_raw 13166 0 - Live 0x0000000000000000
k10temp 13166 0 - Live 0x0000000000000000
lp 17799 0 - Live 0x0000000000000000
parport 46562 3 parport_pc,ppdev,lp, Live 0x0000000000000000
usbhid 47198 0 - Live 0x0000000000000000
hid 95463 1 usbhid, Live 0x0000000000000000
ahci 26002 3 - Live 0x0000000000000000
libahci 26861 1 ahci, Live 0x0000000000000000
r8168 215626 0 - Live 0x0000000000000000
xhci_hcd 82820 0 - Live 0x0000000000000000
```

```
lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9640
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

---

