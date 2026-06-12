---
title: "Improving AWN Function in Compiz"
date: 2009-12-15
forum: Desktop Environments
---

### Post by promet on 2009-12-15
Hey,


I was having a good amount of trouble getting AWN (Avant-Window-Navigator) to render properly within Compiz, AWN bar disappearing when the cube rotated to a new desktop screen, etc.


I found a very useful tip while searching the forums that has helped me immensely. 


GOTO - Main Menu -> Preferences -> CompizConfig Settings Manager -> Desktop -> Widget Layer


If you do not have this enabled yet, go ahead and enable it. 


Then, click on Widget Layer and go to the "Behavior" tab and type the following into the "Widget Windows" field:


```
name=avant-window-navigator
```


This, has, from what I gather, given AWN it's own widget layer in Compiz, which keeps the rendering from getting confused as Compiz goes about doing its sexy, fantastic thing.


This has solved most, if not all, of my flicker, re-draw, etc. issues with using AWN in Compiz, which is awesome...


Also, I would like to thank the guy who posted this initially, I could not for the life of me find his post again, which led me to post this and bring this solution up in visibility.


I think it is key. So, thank you, Post of the Unknown Soldier; I salute you!


Hope this helps!

---

