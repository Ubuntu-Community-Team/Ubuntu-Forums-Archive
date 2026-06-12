---
title: "how to disable &quot;aero snap&quot; function when dragging windows to screen edges?"
date: 2011-05-02
forum: Desktop Environments
---

### Post by 13east on 2011-05-02
i would like to disable the aero snap function when using the mouse to drag a window to screen edges... i like to keep multiple small windows with various sizes at the edges of the screen (i.e. with media players listening to music or watching videos to have the screen in one corner while using the remainder of the screen for something else)

i would still like to keep this function with hotkeys...
(<super> + up/down/left/right)

is there any way to work around this?
any help would be very much appreciated...
thank you

---

### Post by Krytarik on 2011-05-02
These are features of Compiz' "Grid" plugin, it seems not possible to disable the 'Aero Snap' feature but keep the shortcut features, you can only disable it completely:
"CompizConfig Settings Manager -> Grid".

If you don't have CCSM already installed, "compizconfig-settings-manager" is in the official repos.

Greetings.

---

### Post by 13east on 2011-05-02
> **Krytarik said:**
> These are features of Compiz' "Grid" plugin, it seems not possible to disable the 'Aero Snap' feature but keep the shortcut features, you can only disable it completely:
"CompizConfig Settings Manager -> Grid".

If you don't have CCSM already installed, "compizconfig-settings-manager" is in the official repos.

Greetings.

thx for ur suggestion... and it solved all my problems

under CCSM -> Grid -> Edges Tab -> expand Thresholds section:
- set all thresholds to "0" to disable mouse windows snap but the hotkeys still work
- the default thersholds are too large and thats why i was having so much problems; if you set it "1" the snap behavior is not as sensitive and works like a charm

thx again Krytarik

---

### Post by Krytarik on 2011-05-03
> **13east said:**
> 
under CCSM -> Grid -> Edges Tab -> expand Thresholds section:
- set all thresholds to "0" to disable mouse windows snap but the hotkeys still work
- the default thersholds are too large and thats why i was having so much problems; if you set it "1" the snap behavior is not as sensitive and works like a charm

Uh, that underpins my intention to really check Natty for myself, at least with a liveCD, because in every screenshot I saw there was only a "Bindings" tab. I was indeed wondering how there is a feature without any kind of options to set it up.

Thanks for the info, and great that it is possible the set up separately!

---

### Post by anaconda on 2011-05-20
Thanks for this incredibly helpful solution.

The aero snap feature was reaaaally annoying, because almost always it happened it was not meant to happen...

---

### Post by 13east on 2011-05-20
> **anaconda said:**
> Thanks for this incredibly helpful solution.

The aero snap feature was reaaaally annoying, because almost always it happened it was not meant to happen...

it always annoyed the hell out of me too... but i never knew the settings for snap function was there... now i use both keyboard and mouse shortcuts all the time :D:D:D

---

### Post by nrundy on 2011-05-20
> **13east said:**
> i would like to disable the aero snap function when using the mouse to drag a window to screen edges... i like to keep multiple small windows with various sizes at the edges of the screen (i.e. with media players listening to music or watching videos to have the screen in one corner while using the remainder of the screen for something else)

i would still like to keep this function with hotkeys...
(<super> + up/down/left/right)

is there any way to work around this?
any help would be very much appreciated...
thank you

How did you get <super> + left/right to "snap" the window to the side? It doesn't do this by default right?

---

### Post by 13east on 2011-05-21
> **nrundy said:**
> How did you get <super> + left/right to "snap" the window to the side? It doesn't do this by default right?

- CompizConfig Settings Manager -> Grid -> Bindings Tab:
check the screenshot attached; you can use that to grab hotkeys to whatever shortcut you desire.

---

