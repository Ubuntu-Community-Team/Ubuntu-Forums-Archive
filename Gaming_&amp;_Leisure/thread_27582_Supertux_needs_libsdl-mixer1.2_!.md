---
title: "Supertux needs libsdl-mixer1.2 ?!"
date: 2005-04-16
forum: Gaming &amp; Leisure
---

### Post by Turin Turambar on 2005-04-16
Synaptic says that

The following packages have unmet dependencies:
supertux: Depends: libsdl-mixer1.2 (>= 1.2.5) but it is not installable

What shall I do?

---

### Post by mariuss on 2005-04-24
I have Supertux installed no problem, including libsdl-mixer. There is no sound though :-(

Any hints on how to enable sound for this game?

---

### Post by NeoChaosX on 2005-04-24
Turin: It should be installable. Have you enabled the other apt repositiories?

mariuss: Tried enabling Sound and Music in the options menu?

---

### Post by Turin Turambar on 2005-04-24
Thanks everyone. I solved this problem. Yes, sources.list didn't have everything set. :)

---

### Post by mariuss on 2005-04-25
The game's options menu has both sound and music disabled :-(

I do have sound on the system though (system sounds, mp3 play back, ...)

Marius

---

### Post by rage.callao on 2005-05-30
having the same problem as marius even after reinstalling the game

---

### Post by rage.callao on 2005-05-30
seems like i found a solution in the other threads. need to install [COLOR=Red]**libsdl1.2debian-all**[/COLOR] and sound now works with supertux and foobillard.

---

