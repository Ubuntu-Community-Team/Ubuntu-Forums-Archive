---
title: "Wine Screwed Up Refresh Rate"
date: 2006-10-26
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2006-10-26
I just tried to run WoW in wine 0.9.22 that I got from the repositories, as I expected, it didn't work.  Before I ran wow, I, with no problems, configured my display to use 1024x768 res at 60 Hz refresh rate.  After exiting WoW, which failed because of graphics issues, my res got set to 1280x1024, refresh got bumped up to 85 hz, and even after running dpkg-reconfigure xserver-xorg and resetting all of my original settings, the only refresh rate available to me is 85 hz.  Can someone tell me how to restore the other refresh rates as options?

---

### Post by God Of Atheism on 2006-10-27
I don't have a solution, but a similar problem. Diablo II LOD is started fullscreen at a refresh rate of only 60 Hz where I'd prefer 85 Hz. Of course I can change my desktop resolution to 800x600 or so and run in windowed mode, but I'd prefer to run it fullscreen at a higher refresh rate. I tried both the XP and the 2000 emulation to no effect.

---

### Post by wWales on 2009-06-29
in a similar experience, my wine messes up my refresh rate while launching d2LoD, now im using a workaround of [opening another terminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands) and type:

```
xrandr -r 60
```Dont know if it might help you

---

