---
title: "No wallpaper, except a flicker on startup."
date: 2010-09-14
forum: Desktop Environments
---

### Post by Dangerouge on 2010-09-14
Hi! I'm using 10.4 and it was working great, after some minor tweaking. Anyway, then I wanted it to have a cooler outfit so I went for AWN, and it worked even greater. Then I found a guide on how to install GTK-RGBA, and did that in hopes of translucent windows however, the first thing I notice after logout&login is that my wallpaper only flickers once at startup then disappears. All the icons on desktop are where they should be, the background is just white. I've tried changing the background image, but to no prevail, it just takes even all the icons off the desktop and starts flickering some windows on the toolbar. I've tried killall nautilus, with the same results. How can I recover my lost wallpaper, the thing looks pretty gloomy with just gray background...

---

### Post by Dangerouge on 2010-09-14
Heh, nevermind, this was unpredictable (NOT). Everything works out just fine now that I removed anything related to RGBA.

---

### Post by nilarimogard on 2010-09-14
Nautilus needs a patch to work with RGBA, that's why this happens. But the RGBA PPA should have this patched nautilus...

---

