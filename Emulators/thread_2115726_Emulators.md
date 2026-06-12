---
title: "Emulators"
date: 2013-02-13
forum: Emulators
---

### Post by Umbra Diaboli on 2013-02-13
Hello,

Could anyone recommend the best N64, SNES, and GBA emulators for Ubuntu?

Also, does anyone know if it's possible to use the PS3 controller with the emulators?

Thanks a lot!
***Umbra Diaboli***

---

### Post by doorknob60 on 2013-02-13
N64: Mupen64plus. If you want a GUI, try m64py
SNES: Try Snes9x (with the GTK interface, not sure if it's separate or bundled in Ubuntu repos). Another good one is Zsnes.
GBA: VBA-M (VisualBoyAdvance-Merged)

PS3 controllers should work, but I've heard that the analog triggers can potentially confuse some emulators if you want to map to them (L2 and R2). Not sure if that affects all emulators though. There should be some option to disable analog buttons/triggers if necessary. Driver wise, it should work by default with USB, and will also work over USB if you pair it (there are programs to do that).

---

### Post by LillyDragon on 2013-02-16
Some (wired) third-party PS3 controllers are also HID-compliant, so they can act as normal PC controllers when hooked up to a USB port.

As for analogue triggers, those are always finicky on Linux since they're detected as axis' instead of mapped buttons, and are not centered in a resting position by default, so they're usually triggered whether you push down on them or not.

It's sad, but I have to avoid using the triggers on my XBOX controllers when booted in to Linux, which sucks because a lot of games I play rely on them. If there's a way to remap them, I wouldn't know it. However, with PS3 and 360 controllers, you at least have shoulder bumpers, so that's almost guaranteed to behave.

Also, I'd actually recommend ZSNES over Snes9x. The latter is simply slow to get running on Intel hardware, and has a finicky interface; I actually get better performance in BSNES. (Still can't configure it to stay at a stable frame rate though, it keeps playing three times faster than it should!)

ZSNES's UI may not integrate into the OS's, but it at least works. And if you have to have perfect, flawless sound, and have a beefy CPU under the hood, I'd go with BSNES hands down.

---

### Post by DiabolicalClaptrap on 2013-02-17
For SNES/GBA, there's always mednafen. Mednafen can run games via context menu and terminal. Configuration is largely terminal based. If you prefer a GUI for everything, use VBA & snes9x.

Edit: If you're using a controller, I recommend Mednafen (based on my experience with an xbox 360 controller). VBA failed to recognise my device. Just something to keep in mind.

---

