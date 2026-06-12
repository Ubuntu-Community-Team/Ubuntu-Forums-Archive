---
title: "sixaxis controlls to sensative?"
date: 2011-10-02
forum: Gaming &amp; Leisure
---

### Post by runny6play on 2011-10-02
so I've been trying to set up some emulators on my pc.  I want to use my PS extra sixaxis controller. No matter what i do (yes i have tried jscal) the controller analog sticks are too sensitive and whatever input plugin or sections of the emulator just ends up accepting a value as soon as you press the button (ex. zsnes, project 64). Ive managed to get some emulators working by manually editing there .cfg (zsnes) files but in some others i can't (project 64). is there any advice on how to fix this?
p.s. so far when ive asked for help here ive gotten ignored. I don't if it was because of the subject matter or something i am doing.
(

---

### Post by survient on 2012-01-06
A little late to the party but I think I know what you're talking about. If you get that difficulty setting the controls in project64 or whatever, run jstest on the command line and see what's going on. Chances are the joystick axis are freaking out and throwing in random values. I think this has to do with the actual SixAxis motion crap causing issues. To fix I just unplug and replug(this causes the joysticks to stabilize in jstest), quickly map my settings, and then I'm good. The other thing I can think of is using a different driver for the sixaxis, probably one that properly recognizes the SixAxis motion jimbob and just being really careful when mapping. Hope this helps.

---

