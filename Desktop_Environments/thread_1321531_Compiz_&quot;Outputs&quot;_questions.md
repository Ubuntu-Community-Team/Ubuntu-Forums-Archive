---
title: "Compiz &quot;Outputs&quot; questions"
date: 2009-11-10
forum: Desktop Environments
---

### Post by gfixler on 2009-11-10
I have an odd setup that has one video card go to a Matrox TripleHead2Go Digital Edition, which is essentially a splitter box with 1 DVI-in going to 3 DVI-outs. The practical upshot is the video card and system see a single, max 3840x1024 display (the Matrox box), and the Matrox box splits that wide signal to 3 max 1280x1024 monitors, which I have hooked up to it (Dell flat panels). It works well, but initially one of the annoying bits was that nothing respected the edges of the screens. There's a Windows driver that comes with the TH2G, but nothing for Linux. Thankfully, Compiz had added overlapping outputs handling (CCSM->General->Display Settings->Outputs). I added these outputs to it and deselected "Detect Outputs":

1280x1024+0+0
1280x1024+1280+0
1280x1024+2560+0

Now compiz respected the monitor borders, and maximizing or fullscreening works beautifully. Everything swells to fill whatever monitor it was on. I even wrote some shell scripts to let me hotkey windows to hop between monitors. Neat.

However, the downside is that while I can manually scale things beyond the boarders, and it's all nicely 3D accelerated across them all, I can't automatically expand things to fill all 3 screens, and certain things act funny, like unfolding the cube. I see the unfolded deal on each monitor, but it's like 3 separate ones that will refold up to reconnect when I let go. If I maximize movies, that works, but if I maximize from Firefox, they go to the left monitor, but swell to fill all 3, which means monitors 2 and 3 don't show anything, and I just see the left edge of the movie poking in the right side of the left monitor, and the rest is black. There's no way to show the rest. It's clipped by the edge of the output.

Now I just tried to use xwinwrap to play glmatrix over the background - same deal. It shows up over the left screen, even over the background image (as if part of it), and under the still-usable icons (nice!), but the middle and right screens show nothing. It's all on the first (left-most) output. When I use Compiz's zoom, it only zooms the monitor I'm over. If I middle-click the background of a non-zoomed in display while another is zoomed at all, the zoomed one pops back to non-zoomed instantly, and rotate works fine. If I let go, once the cube finally returns and stops moving, that display pops to the previous zoom level. If I try to do that over the zoomed monitor, or rotate the cube by flicking the mouse wheel, the whole cube goes pure white and spins and then pops back to the right colors. It's certainly all a bit wacky. I can initiate the wheel-roll spin and if at any time while it's still in motion I roll over a zoomed display, it also turns all white.

Is there any way to circumvent the trapping of things to one monitor (output) at-will? I can remove the outputs from the CCSM, and then it would work, but then nothing would respect the monitor borders. Everything would fullscreen across all 3 screens, eg. I'd love to understand this Outputs stuff better.

Thanks!

---

