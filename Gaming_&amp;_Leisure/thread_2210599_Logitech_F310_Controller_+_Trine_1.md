---
title: "Logitech F310 Controller + Trine 1"
date: 2014-03-11
forum: Gaming &amp; Leisure
---

### Post by converted on 2014-03-11
After reading some suggestions here and elsewhere, I settled on the Logitech F310 - first game controller I've ever used under Linux.

I've only tried it on two games so far - Trine (not Trine2) and Dust: Elysian Tail.

It works perfectly under Dust (via Steam), no fooling around required.

Under Trine - which was what I really wanted it for (so my son and I could play together easily) - unless I put it in "Direct" mode, it doesn't detect the controller at all.  This would be fine, but although it then detects and allows me to select it - nothing at all works.  If I go in to adjust the bindings, it doesn't actually pick up on any of my controller presses or joystick moves when I try to adjust.  (I can get it to wait for input - but it registers none of the input I provide.)

Any chance that anyone has seen this before or has any ideas?  Googling has been tricky, since most everything is about Trine 2 now...

I'm running 14.04 GNOME edition, but this doesn't seem like the kind of issue that has to do with being on a prerelease to me.  

I'd guess the rest of my hardware is probably not relevant to this, but happy to provide details if needed.

TIA!

---

### Post by efflandt on 2014-03-14
Have you tried jstest or jstest-gtk to see if all switches and levers respond? Although, that does not tell you what games specifically use.

I have an F710 (wireless) which I would think would work similarly if not identical to the F310. In Steam big picture it worked without changing anything (to qualify as potential Steam hardware beta tester). The only game I tried it in was Salvation Prophecy, and only for space flight/combat (still used familiar WASD keys and mouse for walking/ground combat). With the switch on one position Ubuntu recognized it as Logitech Rumblepad and the controls were all mixed up. In the other position it was recognized as a xbox controller and all switches and buttons worked properly except the Dpad strangely worked in circular menus, but not while flying. Since the game had no gui for gamepad setup, I used the Dpad to set some unused things in gui keyboard setup, then modified the gamepad config file to match those presses for left/right (weapon slot selection) and up/down (zoom). Then everything worked fine including Dpad. This was all in regular 64-bit 12.04 (Unity desktop).

I also used used the F710 as an RC controller to try an RC Simulator that someone posted about here, since I forgot where I put my USB RC simulator controller. Although, the configuration for that simulator allows you to set which ever levers/axis or buttons you want for controller functions.

---

### Post by spectatorx on 2014-03-14
I think you should contact frozenbyte on it. They are in process of pushing trine 1 linux to steam. Go to their forums on frozenbyte.com or to steam forum of trine 1, one of developers will answer to you within maximum few days. Also good thing will be to contact their support via email: Support [at] Frozenbyte [dot] com.

---

### Post by ra-censhare on 2014-03-14
same feedback here from my side - I just pluged in my Logitech F710 and started playing without any issues - under Steam (Don't Starve, Supermeatboy).
But outside from steam (e.g. my media library) the gamepad is not recognized as well as it is working together with steam.
IS this some miss-configuration on my side or is it just steam being able to detect and set the gamepad properly?
thanks for enlightenment.

---

### Post by converted on 2014-03-20
Thanks everyone - I didn't mean to abandon the thread, just got busy for a few days.  I will try some of what has been mentioned + also go to Frozenbyte if I can't work it out.

Appreciate the help!  :-)

---

