---
title: "How to configure my gamepad, Qjoypad"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by N00b-un-2 on 2008-09-21
I have a Playstation Dualshock style usb gamepad.  It's a a Saitek P990 Dual Analog Controller.

href="http://www.amazon.com/Saitek-P990-Dual-Analog-Game/dp/B000AL703E/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1222023788&sr=8-1  

It comes with a standalone program that you install with the driver in windows that allows the game pad to emulate keystrokes and mouse movements using any of the six axis.  It works beautifully in Windows XP and I can even use it to control my computer using the analog control sticks to move the mouse cursor.
I've been trying to find a program that will allow me to do so in Ubuntu.  I've already installed the joystick drivers and the gamepad works properly and is recognized by Ubuntu.  I've also installed jscalibrator and calibrated the gamepad.
In my searches I've come across only one program that comes close to approximating what the Saitek SST software does (emulating keyboard and mouse functions with the gamepad) and that's Qjoypad.  I installed qjoypad and aside from the initial setup being quirky and the fact that all the alphabetical characters can't be used (you can set them but the configurator won't register any change), and for some reason it seems that a run of no more than 4 keys (asdf, qwer, 1234, etc.) can be used or else the whole calibration resets itself.  Weird...
Anyway, I like to play FPS games using what I've always referred to as "Turok" controls (from the N64 game).  Basically you use the right control stick to move fore and aft, and lateral stick movement strafes port or starboard (left and right, respectively) and the left control stick has the vertical axis reversed but the horizontal axis retains it's normal left=left/right=right orientation.  This setup is commonly know as "Legacy Southpaw" on many modern FPS console games including the Halo series and Call of Duty 4 to my knowledge.
Now my issue is this.  After assigning keystrokes and mouse movements to my gamepad, all of the digital inputs work fine (keystrokes and mouse buttons) but the mouse movement which I'm attempting to control with the left analog stick is pretty much all or nothing, and Qjoypad emulates mouse movement like a single digital keystroke, without a continuous/varying input.  For example, using Qjoypad i can control the mouse and move the cursor around the OS, but it moves in single increments of set amounts of pixels proportional to the "mouse speed" setting on the Qjoypad configuration panel.
So what I'm asking is this:
Is there any program that will allow me to properly control my mouse using the analog control sticks on my gamepad?
Is there any way to use ndiswrapper to install the windows driver and software in Ubuntu?

---

