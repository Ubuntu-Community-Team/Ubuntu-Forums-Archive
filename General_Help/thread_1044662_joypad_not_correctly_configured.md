---
title: "joypad not correctly configured"
date: 2009-01-19
forum: General Help
---

### Post by sergio.ub on 2009-01-19
Hallo, please someone help me..

I have a USB joypad, and exactly [this]("http://www.speed-link.com/?p=2&cat=312&pid=3182&paus=1") model. It has two analog sticks, a digital pad and 12 buttons.

Well, it's recognized as "Dragonrise generic" by joydev module and mapped in /dev/input/js0. Apparently all things seem ok.

But when i load a game (linux based or wine emulated) it has a very strange behaviour (buttons and axes doesn't work or work incorrectly).

the explanation arrives when calibrating the joypad (using kde4 systemsettings or jscalibrator).
1) the device seems to have SEVEN (???) AXIS
2) the y axes of the left stick in mapped contemporarily on the 1st and the 3rd axes of the driver (???).
3)the second stick seems completely useless, but moving it, it activates the same signal of button 2 and 4 (??? again)
4)10 buttons send normal signals, the other two are useless.
5) force feedback is completely ignored.

Well, i have two plane questions for who can help me.

1)can i use a tool or try manually to modify any kind of config file to force the autodetection to another joypad model (having a list of joypad/sticks to browse in) or map correctly axes and buttons?

2)is there any email of "joydev" module developers whom i can write, to collaborate in patching that module?

please send me a hint..

thanks

---

