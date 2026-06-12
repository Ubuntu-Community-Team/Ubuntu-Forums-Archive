---
title: "Sound interruption in Warsaw (Natty)"
date: 2011-06-25
forum: Gaming &amp; Leisure
---

### Post by silex89 on 2011-06-25
I downloaded last night to train again since my friends are organizing multiplayer games in the university. Everything went fine with the download and the installation, I clicked on it and the sound is.... delayed?. It's like playing a song at a 0.8x instead of 1x, and sometimes the sound just cuts and returns "in time" but with the same speed....

I'm using Natty with Unity, PulseAudio driver (for some reason the sound module in the game's setup is "qf", I can switch it to OpenAL but I have no sound).

Here's the output when I do "lspci -vnn"

```
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Acer Incorporated [ALI] Device [1025:048b]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```



Any ideas?


Regards :)

---

