---
title: "Gamepad Problem, anyone else have a Logitech Dual Action Pad?"
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by SleepWalkerX on 2007-10-22
I tried searching, but I couldn't exactly find a similar problem.  

The pad registers just fine.  Its almost perfect except for a slight problem with the dpad.  When checking /dev/input/js0 with jscalibrator it seems that the DPad is registered as an axis and not a button.  This makes it rather difficult when trying to map "Up" on the DPad to move forward.  

Is there anyway to map the DPad directions (up, down, left, right) on this controller to buttons?

edit:  Another question is, do any of you guys have a gamepad whose Dpad controls register as buttons that you'd recommend?

---

### Post by acoustibop on 2007-10-22
Don't use jscalibrator, SleepWalkerX.  It has a nasty habit of disabling your directional controls, and may be responsible for your present problem.  Does your controller work Ok in games with jscalibrator completely removed?

---

### Post by SleepWalkerX on 2007-10-22
Actually I tried to use the controller before I had installed jscalibrator and it was giving me problems.  I never fully used jscalibrator on my gamepad.  Specifically, the game is GTA: San Andreas through wine. 

It seems like it would work fine besides the Dpad.  Like the two bottom analog controls work perfectly and view around the character.  Every actual 'button' seems to be registering fine in the controls.  The only problem is that darn Dpad.  

Well and that my character is constantly moving forward, but that's different problem, heh.

edit: Just want to kinda specify for other people, the Dpad works, but I can't map the directions on the gamepad in game.

---

### Post by SleepWalkerX on 2007-10-22
Ok it seems like I just needed a reboot.  Now I don't have to map the control to move forward but pressing up on the dpad moves forward.  Success!  

Now just have to work on wine and having dual output, hehe.  Sweet stuff though, it works.

---

### Post by Indubitableness on 2010-06-07
I know it's been a long time but any chance you can post your joystick.cfg for half-life2?

---

