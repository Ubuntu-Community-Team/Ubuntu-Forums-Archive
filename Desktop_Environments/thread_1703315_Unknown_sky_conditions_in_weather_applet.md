---
title: "Unknown sky conditions in weather applet"
date: 2011-03-09
forum: Desktop Environments
---

### Post by Zero2Nine on 2011-03-09
Currently I use the weather applet from the Gnome panels and I'm happy with it, except for one thing: It won't display sky conditions properly in the case of a clear sky. Then it just displays "unknown" (while the icon shows a sun or a moon without clouds). If the sky is cloudy this is displayed correctly in text.

If the weatherapplet uses the same data as weather-util I understand why. Typing ```
weather-util -i MYSTATION
``` does not give sky conditions at all when the sky is clear.

This is how it is displayed now:

```

   Temperature: 46 F (8 C)
   Relative Humidity: 75%
   Wind: from the WSW (240 degrees) at 18 MPH (16 KT)
   Weather: haze
   Sky conditions: overcast

```

And this is how it should be. But sometimes Weather and Sky conditions are simply missing from the results.

---

