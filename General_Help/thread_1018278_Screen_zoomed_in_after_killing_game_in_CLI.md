---
title: "Screen zoomed in after killing game in CLI"
date: 2008-12-21
forum: General Help
---

### Post by BWF89 on 2008-12-21
When I play Nexuiz my computer will freeze up when I try to exit the game by using the quit button. Which requires me to do a hard restart.

I tried to get around this problem by instead of exiting the official way hitting CTRL+ALT+F6, using the "ps -e command to list all of the processes running, and than entering "kill xxxx" (the x's representing the process number Nexuiz is using) from inside the terminal.

It worked but when I exit the CLI by hitting ALT+F7 my screen is still set at the 1600x1200 resolution I normally have it set at. But the screen is very zoomed in.

I tried to fix this by going back into terminal and entering "xrandr -s 1600x1200" which is supposed to change the resolution. But according to my computer I'm already using that resolution. It's just that for some reason everything is very zoomed in. I know it's zoomed in because when I put my mouse towards the edges of the screen it moves to another part of my desktop. Because it won't show the whole thing at one time. Which requires me to log out and log back in to get back to the default settings.

Is there some way to disable this zooming effect after I exit Nexuiz so I don't have to log out and than log back in? Besides switching from the copy of Nexuiz that's in the Ubuntu repositories to the one that's downloadable from their official website?

---

### Post by BWF89 on 2008-12-25
Bump.

---

### Post by cb951303 on 2008-12-25
try and find the resolution with ctrl+alt++ and ctrl+alt+- (+ and - from numpad), it always worked for me for what the problem you explained

---

### Post by BWF89 on 2008-12-28
> **cb951303 said:**
> try and find the resolution with ctrl+alt++ and ctrl+alt+- (+ and - from numpad), it always worked for me for what the problem you explained
Thank you.

---

