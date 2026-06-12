---
title: "Looking for a NES emulator that has a &quot;save state&quot; like ZNES does.."
date: 2009-07-20
forum: Gaming &amp; Leisure
---

### Post by hawkeyex on 2009-07-20
But unfortunately, ZNES doesn't support .smc (original NES), and GCFE doesn't do save state...

Any other emulators that'll work in Jaunty or Kubuntu that can make it work?

Thanks!

David

---

### Post by Nevon on 2009-07-20
There is supposed to be save state support, as FCEU has it. But I can't seem to find how to do it. :S

---

### Post by wingnux on 2009-07-20
Mednafen.

---

### Post by BoyOfDestiny on 2009-07-20
I also suggest [mednafen]("http://mednafen.sourceforge.net/"). A couple of nitpicks though. 
It's zsnes (not znes), and it does support smc (short for supermagicom, this is a format of SNES rom dumping, not original NES). 

The standard format nowadays for the original NES/Famicom is iNES format, .nes, or in some cases the .unif format (and for those in the scene long enough, that horrible .prg and .chr format of pasowing, but that is long gone...)

So anyway, grab mednafen from the ubuntu repos, right click your rom, choose open with, mednafen. Press F1 for the hotkeys.

Here are the important ones.

Press alt + shift + 1
Map your gamepad, same style as gfceu it seems. 
(You only need to do this the first time, it will remember the settings.)

Change save states slots by pressing (0-9)
F5 saves
F7 loads
If you press alt + s, this enables "rewind"

It's very cool, hold backspace, and it "rewinds", so if you fall down a pit, you'll fly back out (even the game music plays backwards while rewinding.)

---

