---
title: "Jedi Academy"
date: 2005-11-30
forum: Gaming &amp; Leisure
---

### Post by amunimanghi on 2005-11-30
i have star wars jedi knight: jedi academy. but i enquire a problem. when i want to do a mouse 1-mouse 2 attack (the thing where he spins the saber and attacks) it just switches the saber style or throws it.

---

### Post by Sutekh on 2005-11-30
Does your mouse have three buttons (possibly two and a pressable scroll wheel)??  
If you only have two mouse buttons, pressing them at the same time may simulate pressing the third button.

When I play JA, the middle mouse button (actually pressing the scroll wheel in) changes saber style, and the right mouse throws the saber.  For me pressing mouse1 then mouse 2 will get my character to go through his saber spinning routine.  

Otherwise check the way that mouse clicks are assigned in the game.

---

### Post by MistaED on 2005-11-30
amunimanghi, this is probably due to the emulate third button mode in the xorg config. To disable this, pop open a terminal and go:
> sudo gedit /etc/X11/xorg.conf
And scroll down until you get to something similar to this:
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"Resolution"		"800"
	Option		"Buttons"		"6"
EndSection
(of course it might look a little different on yours to mine, due to me configuring it manually)

The option we want to change is 
> Option "Emulate3Buttons" "true"
Well, you know what to do from here, change this option to false, or just put a hash in front of the whole line like I did. Either way, it should do the trick. Now save the file.

Then you can either restart your computer or hit ctrl+alt+backspace to restart X11, and then try Jedi Academy.

---

### Post by amunimanghi on 2005-11-30
[QUOTE=Sutekh]Does your mouse have three buttons (possibly two and a pressable scroll wheel)??  
If you only have two mouse buttons, pressing them at the same time may simulate pressing the third button.

When I play JA, the middle mouse button (actually pressing the scroll wheel in) changes saber style, and the right mouse throws the saber.  For me pressing mouse1 then mouse 2 will get my character to go through his saber spinning routine.  

Otherwise check the way that mouse clicks are assigned in the game.[/QUOTE]


i check the mouse clicks are. mouse1 is attack. mouse 2 is saber throw. mouse 3 chages style. i did what mistaed said to do but i havent tried it on jkja. does it matter if im using cedega. my friend uses windows and it works fine.

---

### Post by Sutekh on 2005-11-30
[QUOTE=amunimanghi]i check the mouse clicks are. mouse1 is attack. mouse 2 is saber throw. mouse 3 chages style. i did what mistaed said to do but i havent tried it on jkja. does it matter if im using cedega. my friend uses windows and it works fine.[/QUOTE]

I think its less of an issue with Cedega than with X.  Windows must automatically disable the "emulate 3 button mouse" so if you did what MistaED suggested it should work.

---

### Post by amunimanghi on 2005-12-03
i did what mistaed said to. it still doesnt work. im outa ideas

---

