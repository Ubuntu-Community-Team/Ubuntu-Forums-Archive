---
title: "shift + left click - no longer works in Jaunty"
date: 2009-05-01
forum: General Help
---

### Post by Ascenti0n on 2009-05-01
Before Jaunty I could shift and right click the mouse to select multiple layers in PS CS2.

At fisrt I thought it may be a wine issue, but after extensive searching, nothing turned up.

Wondering if key binding or something similar had changed in Ubuntu, I fired up Gimp, and I had the same issues not being able to select multiple layers via shift + r.click.

Out of curiosity, I fired up Krita, a KDE photo app, an there I COULD select multiple layers. I wonder if that is because Krita is wrapped in the KDE DE defaults.

Anywho, I can't be that only person, if it is indeed a Jaunty issue, to have come across this.

Anyone know how to resolve it?

---

### Post by Ascenti0n on 2009-05-01
I tracked the problem down to, what I think is a key-binding issue with compiz.

when I turn off compiz-effects, selecting multiple layers in PS CS2 under wine works fine.

Even though I tried to restore the original settings in compiz manager, the problems remained. So I re-installed compiz after renaming .compiz to .compiz-0, to make it creat a fresh file on re-installation. Sad to say the problem still exists.

So, although I don't like it, I have to work with: appearance->effect->none or re-install Ubuntu (Which I'm not going to do), or reluctantly go back to winXP.

For me, Productivity is vital. Little things like this have a big affect, especially when I can spend hours trying to fix a problem, and for me with this one, it is only half a sollution.

---

