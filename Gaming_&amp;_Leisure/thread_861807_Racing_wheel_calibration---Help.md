---
title: "Racing wheel calibration---Help?"
date: 2008-07-16
forum: Gaming &amp; Leisure
---

### Post by Prosun on 2008-07-16
I am trying to play NFS:Carbon on Linux with Transgaming Cedega, and using my old Microsoft Sidewinder Racing Wheel. The game runs perfectly under Cedega, but the wheel does not. More specifically, the wheel itself, and all of the buttons, work perfectly fine. But when I start a race, I immediately go into full throttle without pressing any pedal, and pressing the pedals does absolutely nothing; Button 3 stops the vehicle. If I go to Options>Controls in the game, the default settings include: Gas>Z axis; Brake/Reverse>Button 3; Left>X axis; Right>X axis. If I select the Brake/Reverse and press the brake pedal, it is assigned to Z axis, and Gas is given no assignment; The same applies for Left and Right.

I then proceeded to attempt to use jstest. With jstest, I learned that my wheel was axis 0, gas pedal was axis 1, and brake pedal was axis 2. Axis 0 worked perfectly: with the wheel turned all the way to the left, its value was -510; with the wheel centered, 0; with the wheel to the right, 510. However, with axes 1 and 2, without any pressure to the pedals, the values for each were 63; with full pressure to the pedals, their values were 0.

Next, I moved on to jscal. I experimented with different values for min, center, and max for the pedals, with only very odd, unhelpful results; for example, I tried min=63, center=31, max=0; if I remember, this made the pedals completely useless. When I tried "jscalc -t..." immediately after "calibrating" everything, I was informed that the axes were not calibrated. Can anyone please help me get my two pedals working in a normal, realistic manner?

---

