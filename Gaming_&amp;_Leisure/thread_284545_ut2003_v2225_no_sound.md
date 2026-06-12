---
title: "ut2003 v2225 no sound"
date: 2006-10-25
forum: Gaming &amp; Leisure
---

### Post by Tycho on 2006-10-25
I have installed unreal tournament 2003 and applied the v2225 patch.
After applying the patch there is no audio. I am running xubuntu dapper with the ati drivers from synaptic. Does anyone know how to get sound working with v2225?

Just to be clear, the audio worked before the v2225 patch was applied.

---

### Post by Tycho on 2006-10-25
Here is an update on what I have done so far -

If I replace the 2225 version of System/openal.so with the original one I get sound in the menu.

If I also replace the 2225 version of System/ALAudio.so with the original one I get sound effects in game.

I haven't noticed any crashes yet by doing this; is this what everyone else is doing to get this working?

---

### Post by collitis on 2007-08-23
For me, just replacing openal.so with the original version got music _and_ effects working.

---

