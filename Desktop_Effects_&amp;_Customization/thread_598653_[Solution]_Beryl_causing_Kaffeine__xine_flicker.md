---
title: "[Solution] Beryl causing Kaffeine / xine flicker"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by leftclick on 2007-10-31
Hi,

I have just installed Beryl on my laptop, and nearly everything works beautifully, but I did have some problem with video playback in Kaffeine / xine which I have now solved.  First here are my relevant specs:

Toshiba Satellite P200
ATi Mobility Radeon HD2600
Kubuntu Feisty Fawn with custom 2.6.22.6 kernel
ATI (FGLRX) drivers 8.42.3
Beryl packages from standard repositories, 0.2.0rc3

The problem I had was that videos would flicker, and the video playback would become detached from the window frame.  It was almost as though Beryl and the video playback window were fighting each other, trying to draw in the same place at the same time (something to do with VSync I think).  I had tried playing around with all the options under Beryl (including VSync and Unredirect) to no avail.

This problem only happened when Beryl was active - with KWin everything worked normally, and I assume it would have been the same with Metacity.  It generally worked okay if the video was fullscreen as well.  So it was definitely a conflict between OpenGL and xine video playback.

The solution was to change the "**video driver**" setting in Kaffeine, under "xine engine parameters" > "video".  I tried every single setting and the only one that works properly for me with Beryl running is "**xshm**".  Of the others, some wouldn't load and all the others had the flicker / detachment problem.

If you use a different video player, as long as it uses the xine engine it should work basically the same way, you'll just have to find the relevant setting.

BTW, this also solved another issue I had been having, which was that some video files (I think lame encoded avis) wouldn't display proper video, instead I got a blur of colours.  These videos now playback correctly once I switched video driver!

Hope this helps, it took me a while to work out.

---

