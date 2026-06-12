---
title: "SDLmame joystick support"
date: 2008-10-20
forum: Gaming &amp; Leisure
---

### Post by TrevorBradley on 2008-10-20
Hey there, new to Ubuntu, long time Slackware linux user.

Running the mythbuntu 8.10 Beta
Running sdlmame 0.123
Joystick is a Logitech Cordless Rumblepad

I'm trying to get my Logitech Cordless Rumblepad working with SDLmame.  It worked well on my old Slackware linux install, and on this new mythbuntu install the joystick works just fine in jstest and jscalibrator.  However, SDLMame doesn't seem to respond to it.

Is the SDLmame package lacking joystick support?  Is there something I can do to force it to use /dev/input/js0?

EDIT: Check that... The joystick is working, but it only recognizes buttons, not UP/LEFT/DOWN/RIGHT or the analog joysticks.  I'm still in a fix and would appreciate some help...
 
Thanks in advance for your help!

---

### Post by TrevorBradley on 2008-10-20
Fixed.  A quick google search shows jscalibrator is the problem.

rm ~/.joystick
Reboot

All good... :)

---

