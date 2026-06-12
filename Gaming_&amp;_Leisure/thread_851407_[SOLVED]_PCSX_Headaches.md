---
title: "[SOLVED] PCSX Headaches"
date: 2008-07-06
forum: Gaming &amp; Leisure
---

### Post by andyhowington on 2008-07-06
I installed PCSX Playstation emulator through Ubuntu's Add/Remove Applications. I understand for it to work you must find the PSX BIOS (which I did) and put it in the hidden folder ~./pcsx/bios, which I did. Also there are plugins that make the video, sound, etc work... and i finally found a bunch of them (like 90) and put them in the ~./pcsx/bios folder... they are .dll files.

However whenever I try to configure , the options graphics, sound, CD-ROM, etc are all **grayed out** even though the plugins directory is set to ~./pcsx/plugins where all those files are. The only thing that isn't grayed out is the BIOS where I have it set to the one i downloaded (something like s---1001.bin).

It is hard enough to find PCSX plugins because a search gives a million results on the PS2 emulator. 

Why can't I set them? How do I find ones that do work? Why isn't ePSXe in Ubuntu's Add/Remove Application thing? 

I have seen explanations for setting this up and they are not noob-friendly. They assume that you already know how all this works. Please help, and don't take anything for granted!

---

### Post by disturbedite on 2008-07-06
try using pSX. it is a better emulator imo & many other people's opinions.
it doesn't require plugins.

---

### Post by FranMichaels on 2008-07-07
Hmm. One, you don't have to have the Sony bios for pcsx, it has it's own internal HLE bios it can use as alternative (which works pretty well) You can of course use the proprietary bios if you wish.

2. You worked too hard! Hunting for plugins is unnecessary. The dll files aren't usable on Ubuntu, and the pcsx-df package already provides a set of plugins. I can tell you it works out of the box.

So I'm wondering, maybe it's worth while deleting your .pcsx folder (backup the bios folder though) go to Synaptic and reinstall the package pcsx-df.

The default setup should look like this, just from installing the pcsx-df package, no tweaking on my part, screenshot below.

---

### Post by flawedprefect on 2008-12-24
I hate to ask, but how do you get those config settings up? I can only seem to find: Configuration Tab>>Plugins & BIOS. I want to slow down the frame rate, and stop my audio from stuttering on CD playback. Also - can I play this at full screen?

---

