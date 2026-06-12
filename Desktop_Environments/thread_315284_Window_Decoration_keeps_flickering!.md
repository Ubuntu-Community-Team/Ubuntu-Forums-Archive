---
title: "Window Decoration keeps flickering!"
date: 2006-12-08
forum: Desktop Environments
---

### Post by nyxynyx on 2006-12-08
hello all! I'm experiencig flickering of window titlebar and borders after i updated my system from the autoupdate and after installing conky. I have to do ctrl+alt+backspace to get rid of the flicker. Sometimes that doesnt work and i have to repeat that again. Any idea whats wrong? I'm using xgl/beryl on my nvidia 6600gt. thanks!

---

### Post by colonel_panic414 on 2006-12-08
Yeah, I've been experiencing that myself, although I haven't installed "conky". I poked around the gnome-system-monitor, and noticed that there were two instances of the Emerald decorator running. It seemed like the two instances were sort of fighting... They would frequently change PID's, making it difficult to stop one. Try swapping back to your normal window manager, then restarting, and swapping back into Beryl. That has helped me, anyway.

---

### Post by nyxynyx on 2006-12-09
yeah you're right there are two instances! Did what you suggested and it's working fine so far... Thanks!

---

### Post by colonel_panic414 on 2006-12-09
Great! I wonder why there are two of the little buggers going? Hopefully the nest updates will fix it when ubuntu.compiz.net goes back online. (idk if you heard, but they had a HDD failure and are currently rebuilding >.> ) Anyway, have fun with Beryl! (It looks really awesome if you customize gnome to look like OS X!)

---

