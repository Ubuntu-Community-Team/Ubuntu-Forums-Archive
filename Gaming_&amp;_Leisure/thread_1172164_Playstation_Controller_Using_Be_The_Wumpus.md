---
title: "Playstation Controller Using Be The Wumpus"
date: 2009-05-28
forum: Gaming &amp; Leisure
---

### Post by propagation_of_sound on 2009-05-28
Hello. I am using a playstation 1 analog controller wired up to a USB adaptor with aim to play the amazing game 'Be The Wumpus' ([http://bethewumpus.sourceforge.net/](http://bethewumpus.sourceforge.net/)). However, I have trouble making the controller interface. The gamepad is recognized, and is /dev/input/js0 (which is the default controller for Be The Wumpus, as I've checked in the source). I've installed jscalibrator, and all the buttons and analog axes work completely in this configuration program. However, when I go into Be the Wumpus, (I've compiled it in debug mode so I know where I am and what is working), none of the axes on the controller make the wumpus move at all. The strange thing is that the roar works (the triangle button), but none of the axes work. 

Can someone help me?

Thanks in advance

---

### Post by rumplefreakinstiltskin on 2009-05-28
Hi,

I'm the author of Be The Wumpus.

Not sure I can help, but I will try.

Have you tried running jstest?

Be The Wumpus uses axes 0 and 3, most likely for your joystick (since I presume rumble doesn't work, as it's not an xbox 360 controller.)

If jstest works, and you can tell which axes are which with jstest, then it *should* work with be the wumpus as well.

-- steve

---

