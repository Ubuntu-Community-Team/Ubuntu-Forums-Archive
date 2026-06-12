---
title: "LTanks: A puzzle/logic game involving tanks"
date: 2009-06-21
forum: Gaming &amp; Leisure
---

### Post by ChaiTan on 2009-06-21
Hi Guys,
I've been working on a 2D tile based game for the past few days. It's a logic game where you are a tank and the goal is to reach the flag by avoiding the Anti-Tanks. It uses data files(graphics and levels) from the Windows game LaserTank. The rules of the game are mentioned on this page:
[http://pages.globetrotter.net/lasertank/ltank_en.html](http://pages.globetrotter.net/lasertank/ltank_en.html)

The game aims to be a clone of LaserTank and has 2030 levels and you can also get more from the LaserTank website . LTanks has been written in C using the cross-platform library SDL. 

To play the game:
Download Linux binaries(32-bit and 64-bit) here.
[http://ltanks.googlecode.com/files/ltanks-lin-0.5.1.zip](http://ltanks.googlecode.com/files/ltanks-lin-0.5.1.zip)
Extract it.
Ensure that you have the necessary dependencies:
```
sudo apt-get install libsdl1.2debian libsdl-ttf2.0-0
```
Execute ltanks or ltank64 depending on whether you have 32-bit or 64-bit Linux.

Keyboard Controls:

Move Up = Up Arrow Key
Move Down = Down Arrow Key
Move Left = Left Arrow Key
Move Right = Right Arrow Key
Shoot Laser = Space
Undo = Backspace
Restart = Enter/Return
Hint = H
Load Level = L
Load Next Level = N
Load Previous Level = P
Note: Don't use the Numpad 

Project Homepage:
[http://code.google.com/p/ltanks](http://code.google.com/p/ltanks)

If you have any suggestions or bug reports please post them here.

---

### Post by ChaiTan on 2009-06-22
Found another port of LaserTank:
[http://sourceforge.net/projects/laserxtank/](http://sourceforge.net/projects/laserxtank/)
But it does not seem to compile using gcc 4.3

---

### Post by ChaiTan on 2009-07-01
Version 0.5 released with following changes:

Added Anti-Tank shooting animation
Added a configuration file
Added Support for custom level files
Added Support for custom graphics (LTG Files)
Added Scaling support
Added support for compressed BMP's
Reduced Memory usage
Some Performance Improvements
Some UI improvements
Added buttons
Tank is now identified as an obstable
Infinite loop bug fixed
Various Other bug fixes.

---

