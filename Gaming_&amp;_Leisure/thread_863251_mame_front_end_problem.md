---
title: "mame front end problem"
date: 2008-07-18
forum: Gaming &amp; Leisure
---

### Post by wildman4god on 2008-07-18
Hey ya'll,
     I am using sdlmame and i want a front end for it and i have serveral front ends working but the problem is when it generates a game list (for the click to navigate front ends not wah!cade) it gives me hundreds of games when i only have a few, how do i get it to only list the ones i have. Thanks in advanced.

---

### Post by DoktorSeven on 2008-07-18
Use kxmame (the SVN version compatible with sdlmame -- a package is available [here](http://sdcofer.googlepages.com/)).  Make sure you properly configure sdlmame to point to your MAME ROM directory, and kxmame should search for all the ROMs you have available; those should be displayed when you click the Available (I think that's what it's called, I don't have it available at the moment) option on the left side of the interface.

---

### Post by wildman4god on 2008-07-19
worked like a charm thanks.

---

