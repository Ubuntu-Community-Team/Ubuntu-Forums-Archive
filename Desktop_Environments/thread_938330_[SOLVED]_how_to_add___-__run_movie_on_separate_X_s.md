---
title: "[SOLVED] how to add   -  run movie on separate X screen  -  to &amp;quot;open with&amp;quot; menu in Na"
date: 2008-10-04
forum: Desktop Environments
---

### Post by estevez on 2008-10-04
Hello,

I'd like to run videos  fullscreen on my TV, configured as separate X screen. And I want launch it from other screen (monitor). It works OK with command:

```
DISPLAY=:0.1 kaffeine -f /home/video/movie.avi
```

BUT. How I can add this command to the nautilus menu "open with"?

I tried add **DISPLAY=:0.1 kaffeine -f** via  file properties - open with - add, but nautilus response is "unable to find app  DISPLAY=:0.1".
I tried wrap this command to the "script", make it executable and add to the menu,  but just kaffeine in fullscreen mode started on TV and no video.

How do I pass argument with filename to the script? Or is there other way?   Or...

Thank you

SOLVED

ah. $1 did the trick :-)

---

