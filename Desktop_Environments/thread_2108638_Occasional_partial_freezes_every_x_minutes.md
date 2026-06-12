---
title: "Occasional partial freezes every x minutes"
date: 2013-01-25
forum: Desktop Environments
---

### Post by qt77h on 2013-01-25
System: EEE 1015PN

VGA: NVidia Optimus (+ Bumblebee)

I have quite the peculiar problem. For a while now (I'm unable to give any more specific date or date it back to an update, sorry), I'm experiencing occasional freezes. 

These freezes are not total but rather only affect the visual output: I can still move the mouse cursor without any noticeable lag or delay and sound keeps playing without issues. 

After a few seconds the system or software "jumps" back into movement. If for example I was playing back a video, the video jumps to the point where it should be according to sound. There's no desync between audio or picture whatsoever.

I've been experiencing these freezes using all kinds of software: VLC, ZSNES, Iron (Chrome) w. regular surfing or watching youtube, using Libre etc.

Changing the graphic mode to Intel or Nvidia didn't change anything either.

Attached you'll find the bumblebee bug report.

**lspci -k | grep -A2 -i vga**

```
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 83ac
	Kernel driver in use: i915
--
04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev ff)
04:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev ff)
	Kernel driver in use: snd_hda_intel
```

---

