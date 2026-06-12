---
title: "Xbox 360 Wired Controller in Hardy Heron"
date: 2008-04-16
forum: Gaming &amp; Leisure
---

### Post by skuller12 on 2008-04-16
Wanted to try my Xbox 360 wired controller in Ubuntu yesterday but instead of plugging it in and seeing if it worked, I went on the forums and installed Xpad per the instructions I could find. Nothing I tried got the controller working. Stupid to get ahead of myself like that because another post says the controller works without any extra configuring. So my question now is can someone tell me how to remove Xpad and return my system to it's original controller set up?

If you can't tell me how to reverse the whole thing, I'd still like to remove Xpad.

---

### Post by heartburnkid on 2008-04-16
If you installed from a .deb file, it should show up in Synaptic; remove it from there (I'd give you the full way to get to Synaptic, but I'm at work on a Win XP machine right now; it's in the System menu, I know that much).

If you compiled from source, you might try going to the source directory in terminal and typing in:

```
sudo make uninstall
```

(I think that's right)

---

