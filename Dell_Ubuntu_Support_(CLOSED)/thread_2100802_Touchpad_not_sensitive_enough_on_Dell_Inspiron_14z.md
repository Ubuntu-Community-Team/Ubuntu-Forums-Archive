---
title: "Touchpad not sensitive enough on Dell Inspiron 14z"
date: 2013-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mc-rpg on 2013-01-02
I bought a Dell Inspiron 14z (N411z) and the machine recognized every piece of hardware out of the box almost perfectly! The only real issue for me is that the touchpad isn't sensitive enough on the machine, to the point of missing some clicks, sometimes several clicks in a row until I finally tap the touchpad very hard (hard to be a touchpad, which should be sensible to taps for clicks). This issue drives me nuts because even though the touchpad of this laptop is known to suck it doesn't suck so bad on windows (on which it never misses a click).

Another issue with it is that it doesn't seem to be very fast even though I have the speed on maximum on the settings. I can live with this but maybe both issues are related to a faulty driver? Anyways, after scourging the web I wasn't able to find anything useful to this situation so I posted it here to see if I have a better luck.

---

### Post by mc-rpg on 2013-01-03
I have to report that this seemed to be a side effect of having the option "disable touchpad when typing" (under system settings>mouse and touchpad) activated. And come to think of it it kind of makes sense since, for example, EVERY TIME I opened the ccsm tool, the search textbox is focused so I typed the name of the setting I wanted (usually the unity configuration plugin) and then moved the pointer using the touchpad but when I clicked it was ALWAYS ignored and I had to tap it again. Maybe the way the driver of this touchpad handled the switch between "typing" and "not typing" was too slow because I didn't have this issue with on my former laptop. I disabled the setting and things are WAY more pleasant now. I hope this helps people with a similar issue.

---

