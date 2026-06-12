---
title: "Compiz + Matrox TripledHead2Go fullscreen issue"
date: 2010-11-29
forum: Desktop Environments
---

### Post by gfixler on 2010-11-29
I have a [Matrox TripleHead2Go]("http://www.matrox.com/graphics/en/products/gxm/th2go/") Digital Edition, which is basically a DVI splitter - one graphics card output is split to 3 monitors, and the computer thinks it sees 1 very wide screen. It theoretically maxes out at 3840x1024 (3 1280x1024 screens), which is the max of my 3 Dell screens anyway. It comes with drivers for Windows, but nothing for Linux, which means that maximizing and fullscreening windows sends them across all 3 screens, because it doesn't understand monitor borders.

Enter Compiz. Compiz Fusion has in its General Options under the Display Settings tab in the CompizConfig Settings Manger an Outputs list, wherein you can override auto-detection of the screen(s) and enter your own geometry strings to tell it where you believe you have displays. I've entered these settings:

1280x1024+1280+0
1280x1024+0+0
1280x1024+2560+0

I put the middle one at the top, as it seems to cause some apps to treat it as the primary screen, so they automatically want to place things to it, though I could be imagining this. What I'm not imagining is that this makes windows handled by Compiz work great. Everything maxes/fulls to the display they're on, yet the whole thing is still OpenGL accelerated as one display, and I even gave myself some hotkeys to enter either the settings above, or just one 3840x1024+0+0, so with a keypress, I can toggle the behavior from separate screens to one giant screen, which can be handy sometimes.

The only remaining problem is trying to view embedded things in Firefox fullscreen. This includes Flash movies and any embedded movie content, which I believe is either handled through Movie Player or VLC, or maybe both depending on MIME type. I think the problem is that these things work outside of the Compiz windowing system, trying to overlay above everything, maybe even writing directly to the video buffer?

What happens is that they do go fullscreen to only the monitor that Firefox is on, but they treat the monitor like it's part of a 3840x1024 display, and justify to the left of the screen. I end up with a giant panel of black across most of the left of the screen (i.e. the empty area to the left of the fullscreened movie), and then just a thin strip down the right side of the screen of the left edge of the movie. It's trying to center itself one screen to the right of the current monitor, but Compiz clips it at the monitor's edge (i.e. the Output setting's edge), so I can't see the movie.

Any idea what I can do to get fullscreen working? I usually zoom in on the screen via Compiz to the movie area and lock it, but that's far less than ideal.

---

