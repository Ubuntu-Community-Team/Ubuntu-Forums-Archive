---
title: "Halflife 2 freezing on load"
date: 2007-11-09
forum: Gaming &amp; Leisure
---

### Post by Dapman01 on 2007-11-09
Loading to the menu in half life 2 is fine, when I try to load the game from the menu to the game it freezes at the last bar.  I used to work just fine, but all of a sudden quit. can anyone help

---

### Post by snkmad on 2007-11-09
What wine version are you using?
Try to use wine 0.9.48, it fix some steam/hl2 bugs.

---

### Post by Dapman01 on 2007-11-09
I'm using 0.9.48
It actually used to work fine with 47, 49 came out but for some reason I can't install it through the syniptic yet

---

### Post by aoanla on 2007-11-09
> **Dapman01 said:**
> I'm using 0.9.48
It actually used to work fine with 47, 49 came out but for some reason I can't install it through the syniptic yet

Indeed - because it hasn't been compiled and packaged for Gutsy yet. Give it a couple of days...

---

### Post by element8 on 2007-11-10
so it gets to the main menu with new/load/options stuff then when you select a saved game it crashes after partially loading? check winecfg to see if maybe something changed after you updated?
by the way the command i was using to play it was:
```
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe \
    -width 1280 -height 800 -applaunch 220 \
    -heapsize 512000 +map_background none -opengl
```

if that helps at all

---

### Post by Dapman01 on 2007-11-10
I upgraded to the new wine today and now it's working fine,

---

### Post by juamez. on 2007-11-14
> **Dapman01 said:**
> I upgraded to the new wine today and now it's working fine,

Do you mean 0.9.49? I have that one currently installed, but HL² is really slow. Still better than when I was using 0.9.46, because HL² wouldn't even start - just like in the topicpost.

---

