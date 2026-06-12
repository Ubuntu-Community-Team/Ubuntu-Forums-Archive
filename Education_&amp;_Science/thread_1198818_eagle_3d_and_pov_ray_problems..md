---
title: "eagle 3d and pov ray problems."
date: 2009-06-27
forum: Education &amp; Science
---

### Post by Caimo on 2009-06-27
I'm not sure if this is the right place or not but recently I wanted to start doing 3d circuits and do some animation so when I do tutorials for the paranormal group I work with, I can show where everything goes and what it'll look like and stuff, but each time I render I get the following errors in pov ray.

File: C:\Documents and Settings\user\My Documents\POV-Ray\v3.6\include\glass_old.inc Line: 18
Parse Warning: Due to changes in version 3.1, you must add interior {I_Glass} to all objects calling glass_old.inc textures and finishes...
File: C:\Program Files\Eagle\ulp\Eagle3D\povray\tools.inc Line: 53
Parse Warning: Fallback font not found. Please specify the path to courbd.ttf in the ini-file
File: C:\Program Files\Eagle\ulp\Eagle3D\povray\tools.inc Line: 79
Parse Warning: Font Courier not found. Fallback font used
File: C:\Program Files\Eagle\ulp\Eagle3D\povray\tools.inc Line: 83
Parse Warning: Font Courier Bold not found. Fallback font used
File: C:\Program Files\Eagle\ulp\Eagle3D\povray\tools.inc Line: 91
Parse Warning: Font Arial Bold not found. Fallback font used
File: C:\Program Files\Eagle\ulp\Eagle3D\povray\tools.inc Line: 95
Parse Warning: Font HandelGo not found. Fallback font arial used
File: C:\Documents and Settings\user\My Documents\eagle\lm555\timer-555-based.pov Line: 214
Parse Warning: Should have at least 2 objects in csg.
File: C:\Documents and Settings\user\My Documents\eagle\lm555\timer-555-based.pov Line: 218
Parse Warning: Should have at least 2 objects in csg.
File: C:\Program Files\Eagle\ulp\Eagle3D\povray\cap.inc Line: 30
File Context (5 lines):
#local cap = object {superellipsoid{<1, 1>scale<diam,diam*0.25,diam>rotate <-90,-7.5,0>translate<0,diam*1.1,0>} }
#local txt = text{ ttf arial_font
Parse Error: Expected 'string expression', undeclared identifier 'arial_font' found instead

I've been looking for days for answers, google, and board after board. Someone said this was the best place.

I use windows xp, a toshiba satelite. I also noticed the renders look like this.

[IMG]http://www.freewebs.com/evps/problems.JPG[/IMG]

---

### Post by Caimo on 2009-06-28
I was able to fix everything but this glass error....

---

