---
title: "Dell Latitude 120L Mic Problem"
date: 2007-12-02
forum: Dell  Ubuntu Support
---

### Post by MRProgrammer on 2007-12-02
I have a friend with a Dell Latitude 120L laptop. We've been trying and trying to get the mic working with it, but the best we've been able to manage is a fuzzy or static sort of white-noise.

We've verified that the mic itself works on another computer. It's plugged into the mic jack, and it's switched on.

Here's some laptop's of the specs.
```
# lspci -v
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Dell Unknown device 01cb
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
```
```
# cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa
```

From that we figured out it's the STAC9200 model, and we added the following line to the end of the "/etc/modprobe.d/alsa-base" file.
```
options snd-hda-intel model=ref
```

In the sound settings, both the capture and digital settings are enabled and at max. We've tried choosing the mic, front mic, and line input selections, but now for some reason we only have the mic input selection. I don't remember what was changed to make it only mic.

We've tried installing the linux-backports-modules from the gutsy-proposed repository. Still no luck. (Installing this might have been what made it only have the mic option in the input selection. I don't quite remember.)

Any help would be greatly appreciated. Thanks in advance.

---

### Post by dinosaur on 2007-12-02
Hey there, I'm the friend. : )

Like MRProgrammer said, any help would be appreciated. :3

---

### Post by MRProgrammer on 2007-12-03
We just discovered that if the mic is plugged into the headphone jack, the microphone sort of works. It's still really fuzzy, although we haven't played with any of the sound settings since trying this. 

The problem with this is that since the mic is plugged into the headphone jack, nothing can be heard, and the headphones don't work in the mic jack. Those are the only two jacks on the computer.

---

