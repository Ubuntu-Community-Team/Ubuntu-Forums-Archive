---
title: "DVD Frames per Second"
date: 2008-12-21
forum: General Help
---

### Post by dstein on 2008-12-21
I use acidrip and HandBrake to encode ripped DVDs. HandBrake encodes to Xvid at 24 frames per second and acidrip encodes at 30 frames per second. These are the default values and I believe the numbers I gave may be rounded. What is the correct framerate? That is, the frame rate of the original DVD. My guess is 24, since I have the setting "same as source" for framerate in HandBrake. If this is the case, does anyone know if there is a "same as source" setting in acidrip? I know acidrip uses mencoder, which has the -ofps parameter, but I believe this takes numeric values and I am not sure if there is a way to set it to automatically use the framerate from source.

Also, in acidrip, I can set the bitrate such that there is a constant bits/pixel that I want. I imagine that this can be done in HandBrake using the Quality slider, which goes from 0 to 100. Does anyone know what bits/pixel these values correspond to?

Thanks. Please let me know if you know a better place to be posting this question.

---

### Post by PocketDog on 2008-12-21
25fps for PAL DVDs, 24fps for NTSC DVDs. Check the table at the bottom of [this page](http://www.paradiso-design.net/ntsc_pal_conversion_faq.html).

---

