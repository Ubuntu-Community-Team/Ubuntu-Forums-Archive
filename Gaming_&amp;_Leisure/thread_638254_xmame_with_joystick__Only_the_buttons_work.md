---
title: "xmame with joystick:  Only the buttons work"
date: 2007-12-11
forum: Gaming &amp; Leisure
---

### Post by aprete on 2007-12-11
I have a newly installed Gutsy system with xmame.  I'm trying to get my joystick to work.  After reading a number of posts I found that "modprobe analog" gets my joystick working and I can calibrate it using Joystick Calibrator.  Its device name is /dev/input/js0.  But when I fire up xmame, the buttons work but not the stick.  I'm stumped.

Under Window$ I ran a program called joycur which allowed the joystick to emulate keystrokes.  This might be a solution if there's an equivalent program under Linux.

And I'm not ready to drink the Wine.

---

### Post by inversekinetix on 2007-12-11
isnt Xmame several versions behind?  every mame i tried on linux had major flaws in it, i would recommend running it under windows, the 64 bit version is sweet, gets the chds running flawlessly.

---

### Post by acoustibop on 2007-12-12
jscalbrator is your problem, aprete.  Unless you're using Kubuntu (the in built Kubuntu version seems Ok), it has this nice little habit of disabling the directional controls of game input devices, although it reads them itself as being Ok.  You need to remove it completely, including its configuration.

---

### Post by aprete on 2007-12-12
acoustibop:  jscalibrator was the problem.  I deleted the .joystick file, then removed the package, then rebooted, before I had a working joystick.  Thanks for your advice.

inversekinetix:  Someday I'll try out Wine and start running some of my old Window$ software there.  You've got quite an impressive piece of equipment!

Mods:  I'm new to this forum.  I don't know how to prefix the subject with [SOLVED].  Please do it for me or tell me how to do it.  Thanks.

---

### Post by disturbedite on 2007-12-13
i know no one asked for it, but if i could offer some advice:
don't use xmame.  its dead and super outdated.  use [sdlmame]("http://wallyweek.altervista.org/index.php").

if you need a frontend/gui use sdlmame w/ [kxmame]("http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402"). (<-- use that build specifically, not any other or the version available in the official ubuntu repos, its too old & doesn't support sdlmame).
you have to compile kxmame tho. if you can't get kxmame to compile try this:
```
./configure --disable-joystick
```(of course that will disable joystick/joypad support, but some ppl have reported that is what is needed to get it compile).

btw, kxmame is faster.

p.s.  of course disabling the joystick would counter what you want to do here, but i thought i'd mention this info any way.

---

