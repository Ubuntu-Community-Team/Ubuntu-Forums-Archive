---
title: "Conky with 30-bit colour"
date: 2019-01-11
forum: Desktop Environments
---

### Post by CatKiller on 2019-01-11
Since both my graphics card and monitor support 10-bits-per-channel, I've configured my xorg.conf to use that. Everything's working perfectly with that (in Kubuntu 18.04) except conky.

I've got two conky displays on this computer, one showing the date and one showing the time. They're nice because I can choose the font and layout easily, and they just fade into the background if you aren't looking at them. It's just text on a transparent background.

Conky still sort-of works with the 30-bit colour, but the transparency doesn't. I'd imagine it's expecting to have 8 bits of transparency, and instead it has 2. With the configuration that works with 8-bits-per-channel, it doesn't clear itself: it just keeps piling on new layers. Setting *own_window_transparent = false* fixes that, but then I get a black box instead of the transparent background.

Every combination of settings I've tried for true transparency or fake transparency gets me either the box or the overwriting, or random stuff from elsewhere on the desktop. I don't need gently fading transparency, just not drawing anything that isn't the text.

Is this possible, or is conky simply too old and janky to be made HDR-aware?

---

### Post by CatKiller on 2019-01-11
Hmm. Everything but conky and steam. That's annoying.

---

