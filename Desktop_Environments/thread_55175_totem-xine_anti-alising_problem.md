---
title: "totem-xine anti-alising problem"
date: 2005-08-07
forum: Desktop Environments
---

### Post by iH8forcedRegistration on 2005-08-07
I'm a long time Debian user who made the switch to Hoary a couple days back when I accidentally broke my partition table.

I watch a lot of video on my computer, usually while I'm doing something else. Under Debian, I'd use totem (although I don't remember whether it was totem-xine or totem-gstreamer), and everything would work just fine. In Ubuntu, totem-gstreamer doesn't work at all, and totem-xine looks awful.

Specificially, totem-xine isn't antialiasing the picture when I resize it. I played the same movie side by side in totem-xine and gxine, scaled to the same size. The totem version was grainy and painful to look at, while gxine did the scaling smoothly.

Oddly enough, when I asked totem to output a screenshot, it produced output identical to gxine.

I don't mind using gxine for everything, but its UI seems to waste quite a lot of space (particularly the stream information box between the movie and controls). As someone in serious need of a better monitor, the wasted space bothers me quite a lot.

Does anyone know how I could either (a) turn on antialiasing in totem-xine or (b) turn off gxine's interface while in Windowed mode?

tia

---

### Post by iH8forcedRegistration on 2005-08-28
Solved my own problems:

- Hiding the ui in Windowed mode is a feature that's going to be added to gxine eventually, according to the gxine lists.
- I fixed the antialias problem in totem by going into Configuration Editor, and setting /apps/totem/deinterlace to false.

---

