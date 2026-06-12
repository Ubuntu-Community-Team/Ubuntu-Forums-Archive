---
title: "Cairo Dock Help"
date: 2009-05-14
forum: Desktop Environments
---

### Post by AnthonyX61 on 2009-05-14
Hi, ive just installed cairo dock... ive got 9.04
and it looks like this: and i dont know how to get it to something normal, not all black and messy,, also when i hover over it a black box comes around it.

How can i fix it ?? thanks!

[ATTACH]113769[/ATTACH]

---

### Post by aslanprrrrrrr on 2009-05-14
Goto System->Preference->Appearance
Then goto Visual Effects Tab
and choose Extra.
You have to have the Extra effects enabled in order for Cairo to work properly since Cairo is dependent on compiz to work.

What is yours set to?

---

### Post by AnthonyX61 on 2009-05-14
i dont have compiz fusion... but evertime i try sto set the extra effects in the appearance it says cannot be enabled.. ive got intel 350

---

### Post by andrea000 on 2009-05-14
from the picture it looks like your rendering is off
I have used cairo dock with out compiz before and it
worked great,There should be a check box under background
that says repeat image as a pattern to fill background 
make sure that is checked.Now with compiz your driver
may be blacklisted try running compiz check there is
a lot of info on it [Here]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by nilarimogard on 2009-05-15
Try not to run it like this: cairo-dock -o but instead, run it like this (Alt + F2):

cairo-dock -c

(that will make it run in cairo mode, not OpenGL mode).

---

### Post by feffo on 2009-06-30
This appens also to me, with compiz activated (ccsm and all effects working ok). I've jaunty and the last version 2.0.6 of cairo dock!!
This is annoying because that appens with and without opengl rendering...
Is there a way to make this rectangle transparent?
Thanks a lot!

---

