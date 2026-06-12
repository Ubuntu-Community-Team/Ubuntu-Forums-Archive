---
title: "Mouse acceleration"
date: 2006-05-24
forum: Gaming &amp; Leisure
---

### Post by Khannie on 2006-05-24
So I've been playing really badly at UT2004 since I switched to ubuntu...and then I copped it....mouse acceleration. So I go into the settings and turn it off (slider all the way to the left), but now my mouse moves too slowly. I have an mx518.

Mouse + acceleration does not make for good FPS gaming, so I'm sure lots of you have it turned off. 

How can I increase the mouse speed further in the gnome GUI?

(I'm happy at the command line)

---

### Post by nanotube on 2006-05-24
well, if you go to System>Preferences>mouse
there are two sliders there, one is for acceleration, the other is for sensitivity. up the sensitivity one, and it ups your speed, without affecting acceleration.

---

### Post by Khannie on 2006-05-24
That's just it...I have the sensitivity upped to the max and it's still very slow. :(

---

### Post by nanotube on 2006-05-24
hmm... try poking around in gconf editor? (applications>system tools>configuration editor) and see if you can find any settings?

---

### Post by Khannie on 2006-05-24
Ok...that seems to have done the trick....but.....

and this is bad....

I now can't maintain a gnome session. I set the acceleration threshold to 1000000 (to effectively make sure it was off), then things started flashing, now I can't maintain a gnome session. "The gnome session manager has aborted". :(

Does anyone know what setting that affects?

Edit: Fixed it with a failsafe session. :)

Thanks nanotube. :)

---

### Post by nanotube on 2006-05-24
glad it worked out. enjoy your fraggin :)

---

