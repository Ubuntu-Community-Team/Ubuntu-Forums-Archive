---
title: "pcsxr: segmentation fault (core dumped)"
date: 2013-02-18
forum: Emulators
---

### Post by Tommy The Cat on 2013-02-18
There error I'm getting when I run pcsx via terminal is pretty much as above, immediately following an attempt at running a disk image of some sort. It does this with all games. The emulator actually runs pretty decently with most games until I go in and try to mess with the config in some way. First happened when I tried to resize my window. Returning settings to default didn't help. No amount of reinstalling/purging would fix this. Then I did a fresh install of Ubuntu 12.10 (for reasons irrelevent to pcsx) and pcsx worked again until i tried to switch out a BIOS file so I can save games in Gex and FF8. Now I'm back to square one. 

What's going on here?

---

### Post by albandy on 2013-02-18
Don't know where is the problem, but if you delete the .pcsx folder the configuration will be recreated when you start pcsx again.

rm -rf $HOME/.pcsx

---

### Post by Tommy The Cat on 2013-02-18
Deleted the .pcsx file. PCSX ran just fine again under the default configuration, but once I try to alter the configuration (for example, using the 7003 bios so I can run FF8), I'm back where I started.

---

