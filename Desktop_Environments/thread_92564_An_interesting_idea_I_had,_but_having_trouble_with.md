---
title: "An interesting idea I had, but having trouble with: Using joystick to control cursor."
date: 2005-11-19
forum: Desktop Environments
---

### Post by Ricapar on 2005-11-19
I've searched around a bit on Google, and I was able to find this:
```
Section "InputDevice"
  Identifier "Joystick"
  Driver "mouse"
  Option "Device" "/dev/input/js0"
  Option "Protocol" "ImPS/2"
  Option "Buttons" "9"
  Option "SendCoreEvents"
EndSection
....
Section "ServerLayout"
  Identifier   "Layout"
  InputDevice  "Keyboard"
  InputDevice  "Mouse"
  InputDevice  "Joystick"
```

I put that into my xorg.conf file, and it did do something, but at the press of any key on the Joystick, the cursor goes crazy, jumping and clicking all over the place.

Anyone have any ideas or suggestions to get this to work? If it makes a difference, I have a Saitek P3000 Wireless Gamepad.

---

### Post by etc on 2005-11-26
Bump because I'd also like to know this.

---

### Post by almahtar on 2005-11-26
Oh now that IS a cool idea.... but I'm also clueless.

---

### Post by 23meg on 2005-11-26
I don't know whether what you want to do is practically doable but the reason the pointer jumps around is that you're stating in your xorg.conf file that you want to use the ps/2 mouse protocol and mouse driver with your gamepad, in these lines:```

  Driver "mouse"
  Option "Protocol" "ImPS/2"
```

---

### Post by etc on 2005-11-26
[QUOTE=23meg]I don't know whether what you want to do is practically doable but the reason the pointer jumps around is that you're stating in your xorg.conf file that you want to use the ps/2 mouse protocol and mouse driver with your gamepad, in these lines:```

  Driver "mouse"
  Option "Protocol" "ImPS/2"
```[/QUOTE]
[http://freshmeat.net/projects/js2mouse/?branch_id=43604&release_id=150597](http://freshmeat.net/projects/js2mouse/?branch_id=43604&release_id=150597)
Could this be used as the driver?

---

### Post by 23meg on 2005-11-26
Yes, it seems is emulates the ps/2 protocol and gives you an xorg joystick driver.

---

### Post by etc on 2005-11-27
[QUOTE=23meg]Yes, it seems is emulates the ps/2 protocol and gives you an xorg joystick driver.[/QUOTE]
So the xorg.conf entry would be 
```
Section "InputDevice"
  Identifier "Joystick"
  Driver "js2mouse"
  Option "Device" "/dev/input/js0"
  Option "Protocol" "ImPS/2"
  Option "Buttons" "9"
  Option "SendCoreEvents"
EndSection
```
or would I leave the Driver as "mouse"

---

### Post by almahtar on 2005-11-27
Cool!  Not necessarily useful, but cool!

Actually, that could be very useful.  You could set up a dedicated gaming box with all your emulators on it, and navigate between the emulators with your controller.

Sweet.

---

### Post by polaren on 2006-04-12
I'm bumping this one!
I have the same problem as Ricapar, and i have used the howto at: [http://cedric.vincent.perso.free.fr/Projets/index.html](http://cedric.vincent.perso.free.fr/Projets/index.html)

My xorg.conf looks like this:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice "Mouse2" "SendCoreEvents"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier "Mouse2"
	Driver "mouse"
	Option "Protocol" "ImPS/2" #_PROTO_ is 'PS/2' or 'IMPS/2' or 'EXPS/2'
	Option "Device" "/dev/j2m_fifo"
	Option "ZAxisMapping" "4 5" #only if you use the 'IMPS/2' protocol
EndSection

```

I don't even know if im using the right protocol (imps/2), but i tought that was the one because the mouse uses it. 

I can move the pointer up and to the right, but not down and to the left (it goes crazy and clicks). The buttons doesn't work either.

If there are other ways than using the JS2mouse software to solve this i would sure be happy :)


Oh, and my gamepad is a Saitek P880 Dual Analog.

---

### Post by polaren on 2006-04-12
Yes i got it to work!

I just edited my xorg.conf so it looked like this:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	**InputDevice "Mouse2" "SendCoreEvents"**
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

[B]Section "InputDevice"
	Identifier "Mouse2"
	Driver "mouse"
	Option "Protocol" "PS/2" #_PROTO_ is 'PS/2' or 'IMPS/2' or 'EXPS/2'
	Option "Device" "/dev/j2m_fifo"
EndSection[/B]

```

As you can see, i changed the protocol for "mouse2" to PS/2 and removed the line "ZAxisMapping". 

IT works GREAT! Weeehooo :)

---

### Post by Chriss.Hi on 2007-07-20
do you use the js2mouse driver for that?

---

### Post by 99bluefoxx on 2007-09-25
can i get a how to for this, but for a microsoft sidewinder 3d pro plus
i cant seem to get to even work with jsconfig...

---

### Post by tenkamuteki82 on 2007-10-18
Me too! Anyone know?:x

---

### Post by amr2205 on 2008-05-10
> **polaren said:**
> Yes i got it to work!

I just edited my xorg.conf so it looked like this:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	**InputDevice "Mouse2" "SendCoreEvents"**
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

[B]Section "InputDevice"
	Identifier "Mouse2"
	Driver "mouse"
	Option "Protocol" "PS/2" #_PROTO_ is 'PS/2' or 'IMPS/2' or 'EXPS/2'
	Option "Device" "/dev/j2m_fifo"
EndSection[/B]

```

As you can see, i changed the protocol for "mouse2" to PS/2 and removed the line "ZAxisMapping". 

IT works GREAT! Weeehooo :)

Thanks! it worked for me! :lolflag:

---

