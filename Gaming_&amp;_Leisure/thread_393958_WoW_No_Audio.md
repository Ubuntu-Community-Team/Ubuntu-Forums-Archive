---
title: "WoW No Audio"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by falk3r on 2007-03-26
World of Warcraft has no audio/sound of any kind. Loading via Wine with the following Audio options set:

```
winecfg
```

OSS Driver Checked (nothing else)
Hardware Acceleration: Emulation
Default Sample Rate: 22050
Defaults Bits Per Sample: 8
Driver Emulation (tried with this checked and unchecked)

I have installed libjack-0.100.0-0 via synaptic, ran the following code:

```
sudo cp /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so
```

and ran some more code to help with an "ALSA issue".

```
sudo modprobe snd-seq
```

Any advice?

Thank you for your time,
 - falk3r

---

### Post by tnunamak on 2007-05-04
I have the same problem. Can someone help!?

---

