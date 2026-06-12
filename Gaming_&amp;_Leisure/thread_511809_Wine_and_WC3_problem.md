---
title: "Wine and WC3 problem"
date: 2007-07-28
forum: Gaming &amp; Leisure
---

### Post by Reneagde222 on 2007-07-28
So I got Warcraft III: The Frozen Throne going in wine...

However it goes at about 1FPS...

My PCs specs are 

2.13GHz Dual Core

2GB RAM

7900GT

I get 100% smooth framerates in huge battles on windows.

I have tried OpenGL mode to increase framerate, but it crashes Ubuntu (no error).

Turning graphics settings down does nothing...

I use this command to run it: 

wine explorer /desktop=tft,800x600 "Z:\media\XP\Program Files\Warcraft III\Frozen Throne.exe" 

Please help!

---

### Post by xubu_caapn on 2007-08-05
post your xorg.conf. i had this same problem and it was fixed by adding glx and dri modules, and my pc specs are about half yours (1.66ghz dual core, 1gig ram, integrated intel...)

---

### Post by Hobo Joe on 2007-08-05
Add this to the end of that line, separated by a space.
```

-opengl

```

---

