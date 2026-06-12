---
title: "Sound Problem in Ubuntu in my PC"
date: 2009-06-17
forum: General Help
---

### Post by asamay81 on 2009-06-17
Hi,

I am using a PC that has Realtek ALC880 sound card. The sound is fine in windows but in _ubuntu the sound is very less even though my external amplifier and internal ALSA package all are in full volume_.

Here are the details of the terminal output with "aplay -l" command

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```and here is the terminal output with the "lspci -v " command (only audio related part)

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
    Subsystem: Hewlett-Packard Company Device 2a29
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ffa3c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```I have installed the ALSA latest version in my PC.

I am seeking help from you all to improve the sound quality of my PC in Ubuntu.

Thanks

---

### Post by asamay81 on 2009-06-23
this issue i am still dark in....

i tried with this [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The terminal output for lspci -v | less returned this output

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 04)
        Subsystem: Hewlett-Packard Company Device 2a29
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ffa3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


Now i was trying to match in alsa whether my sound card is supported..But nowhere I got the option for Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family)..am i doing any wrong to find out whether my sound card is supported or not? please help me o do so...

---

