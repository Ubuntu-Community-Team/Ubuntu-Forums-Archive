---
title: "how to enable rain in compiz"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by kystorms on 2007-07-03
i have a problem which I am not sure is a fault of my graphics card or not
in the compiz manager
in the rain section

when i try to enable it, in the actions section it states disabled, how can i enable it?
or is it that since it is disabled, that i can not use the rain due to graphics card?
I have full cube, everything but rain and snow work....

thanks
graphic card ATI 1000

---

### Post by hyperair on 2007-07-03
If you card doesn't support Pixel Shaders, then you can't run the water plugin, or the blur plugin, just like my case.

However, I don't know why snow doesn't work for you.

---

### Post by kystorms on 2007-07-03
i was thinking it might be a problem with how i downloaded it or something, because most of the keys for each option in comiz work, but some are "disabled" and with rain the key to turn it on is disabled, but not the key for wipers or others...

so if someone could tell me, can i switch the keys to my own choices * ie- <super> any other key * instead the disabled keys....

thanks

---

### Post by hyperair on 2007-07-04
Can. Double click on the text.

---

### Post by Happy_Man on 2007-07-04
I've got the same problem; however, everything else in Compiz runs absolutely perfectly. I'm even using Compiz Fusion and everything runs fine. Except for rain. I have tried Compiz, Ubuntu Compiz, Beryl, and Compiz Fusion. Same problem. When I try to enable it, I see that processor usage starts up, but it hovers around 20%. Something's happening, I just don't know what. It's craaaazy! :D

---

### Post by digital_exhaust on 2007-07-04
I have never been able to get rain to work either....tried everything and nada...

I have come to the conclusion that my card simply won't support it.

---

### Post by hyperair on 2007-07-04
Try ```
glxinfo | grep fragment
```

If it doesn't have any output, then Water, Blur, Reflection won't work. Motion Blur works though.

---

### Post by Happy_Man on 2007-07-05
Blur is like, whatever's behind the titlebar is slightly blurry, right? That works for me, but no Rain! What gives?

---

### Post by hyperair on 2007-07-05
If that's the case then it's not your graphic card that doesn't support it I think. It must be something else.

---

### Post by Happy_Man on 2007-07-05
That's crazy. Are you saying that through Compiz, Beryl, and Compiz Fusion, not *one* of them supports my rain, although every other gee-whiz shiny effect is available. Grrr......

---

