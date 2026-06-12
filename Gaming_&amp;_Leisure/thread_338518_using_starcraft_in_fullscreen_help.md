---
title: "using starcraft in fullscreen help"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by L_o_N_e_R on 2007-01-14
im using cedega to play starcraft brood war installed with no problems :)

the only thing thats bugging me is the full screen mode.....

i want it to strech all the way...instead its only at the corner of the screen


what do i do to fix this?

---

### Post by Frem on 2007-01-14
Edit your /etc/X11/org.conf and add 640x480 under your current colordepth.

Example:
This only shows my Screen section, but it's the relavent part.

```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Note how the "Depth 24" section has three different modes under it. I had to add the last two for WarCraft III and StarCraft, respectively.

Obviously, if you use Depth 16, you'll need to put the modes under there, instead.

Feel free to ask if you need a clearer instructions.

---

### Post by L_o_N_e_R on 2007-01-15
org.conf or xorg.conf?

EDIT: did it.... didnt work....

---

### Post by DARKGuy on 2007-01-15
Try adding the 640x480 under the Depth 8 line, that should do it I guess.

Did you try changing your X resolution to 640x480 then running SC? if you can't change it BUT you have 640x480 added in your xorg.conf at your current bit depth, go to a terminal and type:

xvidtune -prev     -- or --    xvidtune -next

They say to have careful with xvidtune, but I found that -prev and -next do the same thing as Control+Alt+Plus and Control+Alt+Minus :P

---

### Post by L_o_N_e_R on 2007-01-15
didn't work.....

ugh.... i hate playing on windowed mode lol

---

### Post by nevaziah on 2007-03-20
wait, you managed to get starcraft and brood war to work on battlenet? 

I install and update with patch no problem but when I open bnet, it says waiting for connection, then close the game!!!
Can you help me get around that? I will talk to an "expert" buddy of mine when I get home to help with the resolution problem.

---

### Post by Lystrodom on 2007-03-20
I don't think he mentioned anything about b.net. Starcraft has an excellent single player mode, ya know.

Anyway, I installed Starcraft in wine, and fullscreen mode works fine for me.

---

