---
title: "Xorg Multiple keypress events on hold"
date: 2009-04-11
forum: General Help
---

### Post by booljayj on 2009-04-11
X seems to be sending multiple keypress events when a key is held down. This is odd and unwieldy, especially for things such as media keys.

X should only send a single keypress event when a key is pushed down, and a single keyrelease event when it is released. Individual programs should then be responsible for handling cases in which keys are held down.

This can be seen using xev, type it into a terminal and hold down any key, and it will generate a stream of events. For mouse clicks the behaviour is as expected, which makes me wonder why anyone thought that this needed to be done for key presses.

Does anyone have any idea what's going on here?

---

### Post by geraldm on 2009-04-11
Click on
System->Preferences->keyboard
Uncheck "key presses repeat when key is held down"

Just find out where you can assert your preferences.
X just tries to accomodate persons who have differing preferences.
You may have to re-enter the X environment for the changes to have effect.

regards,
Gerald

---

### Post by luisama on 2009-05-04
NOT, nothing to do with keyboard preferences.
Its WRONG, must be a BUG, cant be deliverated.
i know for a fact it dont use to be that way, it must be changed in X 1.6.

*"X should only send a single keypress event when a key is pushed down, and a single keyrelease event when it is released. Individual programs should then be responsible for handling cases in which keys are held down"*

you bet, X should do that... in fact X was doing that for several years.
a lot of software and programs had been written expecting a NORMAL and COMMON SENSE.

that someone press the key A, keep pressed for 5 seconds and release it
NOT EQUAL
to someone press the key A and release it, dozens of time in 5 seconds
PERIOD

---

