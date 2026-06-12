---
title: "snes9express keyboard controlls"
date: 2005-12-17
forum: Gaming &amp; Leisure
---

### Post by The Hedgehog on 2005-12-17
This will probably be a stupid question but i can't find the answer.
How can you change your controls for snes9express when you're using a keyboard?

---

### Post by The Hedgehog on 2005-12-18
Is there nobody who knows how to do this?
I've also installesd gsnes9x. But it has the same problem.
The solution can't be that hard?
Or am I the only who uses a keyboard instead of a gamepad when playing with an emulator.

---

### Post by rykel on 2007-02-19
I just got snes9express to work and am interested to know the answer too... however, I think the keyboard just does not substitute for a controller... it's time for me to go grab one, hehe!

---

### Post by Aglari on 2007-06-21
Yeah, i can't figure it out either. The preset keys are kinda strange, and i'm having trouble setting up my controller too. Blarg.

---

### Post by ziptnf on 2008-06-13
Me neither.  The windows version has the capability to change the keyboard controls.  Why can't this?

---

### Post by bryncoles on 2008-07-24
it is possible... im in snes9express options->controllers->devices, then for 'pad 1 i input what i think is the path to the keyboard: '/dev/input/by-path/platform-i8042-serio-0-event-kbd'. as i understand it, this tells my computer where to look for its joypad input. 

but, when i try and configure the keys i get permission denied! guess ill just use zsnes...

---

### Post by budlite on 2008-09-03
> **bryncoles said:**
> it is possible... im in snes9express options->controllers->devices, then for 'pad 1 i input what i think is the path to the keyboard: '/dev/input/by-path/platform-i8042-serio-0-event-kbd'. as i understand it, this tells my computer where to look for its joypad input. 

but, when i try and configure the keys i get permission denied! guess ill just use zsnes...

No problem with the permission. you just need to sudo snes9express.

But it still complains about:
Pad 1: /dev/input/by-path/platform-i8042-serio-0-event-kbd
Joystick driver too old.

Seems that the kbd driver doesn't compatible to a joystick.

Any workaround?

---

### Post by grossaffe on 2008-09-03
just use the GTK port of SNES9x, its full of win.

---

### Post by budlite on 2008-09-03
> **grossaffe said:**
> just use the GTK port of SNES9x, its full of win.

Thx, i just had a look at it. it seems good:)

---

### Post by Siljrath on 2009-10-23
i dont see it in repo anymore.  stuck with keyboard problems with snes9xpress again, cant see any alternatives in repo.  :p   so much for 9.04.

---

### Post by HarrisonNapper on 2010-03-28
There are alternatives like snes9x-gtk, but snes9express is the most stable for me so far. I've been searching for three days and I can tell anyone who might find this (dead) thread, that there is not a single thread about how to do this. Save yourself some time and find an alternative.

If you're curious, the keyboard key assignments appear to be assigned in ~/.snes9x/snes9x.xml but I don't know what format is being used for the keys.

---

### Post by sven t. on 2010-04-10
snes9express uses snes9x. try /etc/snes9x/snes9x.conf

> 
[Unix/X11 Controls]

...

K00:k = Joypad1 Right
[COLOR=DarkRed]K00:Right = Joypad1 Right[/COLOR]
K00:h = Joypad1 Left
[COLOR=DarkRed]K00:Left = Joypad1 Left[/COLOR]
K00:j = Joypad1 Down
K00:n = Joypad1 Down
[COLOR=DarkRed]K00:Down = Joypad1 Down[/COLOR]
K00:u = Joypad1 Up
[COLOR=DarkRed]K00:Up = Joypad1 Up[/COLOR]
[COLOR=DarkRed]K00:Return = Joypad1 Start
K00:space = Joypad1 Select[/COLOR]
K00:S+d = Joypad1 ToggleTurbo A
K00:C+d = Joypad1 ToggleSticky A
[COLOR=DarkRed]K00:d = Joypad1 A[/COLOR]
K00:S+c = Joypad1 ToggleTurbo B
K00:C+c = Joypad1 ToggleSticky B
[COLOR=DarkRed]K00:c = Joypad1 B[/COLOR]
K00:S+s = Joypad1 ToggleTurbo X
K00:C+s = Joypad1 ToggleSticky X
[COLOR=DarkRed]K00:s = Joypad1 X[/COLOR]
K00:S+x = Joypad1 ToggleTurbo Y
K00:C+x = Joypad1 ToggleSticky Y
[COLOR=DarkRed]K00:x = Joypad1 Y[/COLOR]
K00:S+a = Joypad1 ToggleTurbo L
K00:S+v = Joypad1 ToggleTurbo L
K00:C+a = Joypad1 ToggleSticky L
K00:C+v = Joypad1 ToggleSticky L
[COLOR=DarkRed]K00:a = Joypad1 L[/COLOR]
K00:v = Joypad1 L
K00:S+z = Joypad1 ToggleTurbo R
K00:C+z = Joypad1 ToggleSticky R
[COLOR=DarkRed]K00:z = Joypad1 R[/COLOR]
i had to copy the file to my desktop, edit it and copy it back using the terminal. i think it should work easier - i never used ubuntu before.

---

