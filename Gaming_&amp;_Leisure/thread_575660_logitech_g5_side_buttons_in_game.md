---
title: "logitech g5 side buttons in game"
date: 2007-10-14
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2007-10-14
So, I have a logitech g5 with two side buttons. I have it set up, and everything works great.  Under xev, the side buttons work, under ut2004 they also work(map as button 6 and 7).  under doom3 and wow, they dont.  I cant map them (but I can still map my scroll wheel left/right.  So whats up, how do I get these buttons to work in these games?

---

### Post by bubbalouie on 2007-10-29
Mine work in doom 3 with my MX1000, no need for xev though, I just edited my xorg.conf and found the section that for the 'Configured Mouse' and replaced it with the following:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
EndSection
```

I am not sure this will help you, but I guess it doesn't hurt much to try.

---

### Post by Lodz on 2007-10-31
I am using a G5. Semi worked for me. when i tested my mouse it displayed tilt left as mouse button 4 and tilt right as mouse button 5, however my side buttons remained non-functional. back to researching more clues.

---

