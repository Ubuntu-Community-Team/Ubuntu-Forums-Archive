---
title: "Full Screen Cut Off in (i.e.) Armagettron, lbreakout2"
date: 2008-05-12
forum: Gaming &amp; Leisure
---

### Post by Majiq on 2008-05-12
When running either Armagetron Advanced or lbreakout2 in full screen mode, some of the screen on the bottom is cut off and I can't figure out how to fix it. By some, I mean an annoying amount, like maybe 80-100 pixels or something like that (I can't see the quit option in the lbreakout2 screen). Suggestions?

---

### Post by Perfect Storm on 2008-05-12
1) Disable Compiz
2) Check which resolution the game(s) is set.

---

### Post by Majiq on 2008-05-12
> **Artificial Intelligence said:**
> 1) Disable Compiz
2) Check which resolution the game(s) is set.

I did ```
metacity --replace
``` and the game is still cut off. lbreakout2 does not have resolution options apparent from within the game, but is in full screen mode. The other one was able to be fixed by taking it off the lowest setting and bringing it up to the actual screen resolution, which is 1440x900. I can't seem to find an option for resolution in either lbreakout2 or SuperTux (I know, I didn't mention it before, but whatever).

That said, I'd love to keep my compiz.

---

### Post by Perfect Storm on 2008-05-13
Check your home directory (set it so you can see hidden files). Look through and see if you can find folders with the game(s) name. Usually you can find their config files, then you can edit them and see if the config file have the option to set resolutions.

---

### Post by Majiq on 2008-05-15
> **Artificial Intelligence said:**
> Check your home directory (set it so you can see hidden files). Look through and see if you can find folders with the game(s) name. Usually you can find their config files, then you can edit them and see if the config file have the option to set resolutions.

Nope, no resolution options. Just full screen or not, with respect to the screen. Any other ideas? 

I'm thinking that if they're both based off the same type of environment (I really don't know what I'm talking about here) that maybe it could be a setting that I could change in a more global setting instead of per game. By this I mean that say they were both made using e.g Java (not true), it could be a Java setting.

---

### Post by El Lance-O on 2010-08-13
I too have been having this issue for quite some time now, and I haven't been able to find an answer.

This happens to me with FCEU and OpenMSX amongst other gaming/emulation programs.

Can anyone please put some insight on this?

---

### Post by El Lance-O on 2010-08-13
I actually believe this is an OpenGL problem, as that is the only thing that connects GFCEU, OpenMSX, Armagetron and Ibreakout2.

So what we need to figure out is how to correct OpenGL from incorrectly rendering fullscreen. It seems to think the screen is about an inch lower that what it really is. This is VERY frustrating, making most games completely unplayable.

Anyone?

---

### Post by proteusmoteus on 2010-08-13
Have the same problem with eschalon book 1 and iji (a wine game). Most games expect 4:3 and sometimes 5:4 and 16:9 people get a cropped image. Havent fixed it yet but someone from another forum suggested it was a scaling problem with a graphics card dependent fix.

For an nvidia card you can run the command 'nvidia-settings' to get a control panel. Under 'DFP-0', a label for my flatscreen, one sees scaling options such as centered/stretched/scaled and a 'force full gpu scaling'.

I briefly tried playing with those but had no success. My next attempt will include disabling compiz and seeing if that makes a difference.

---

### Post by El Lance-O on 2010-08-13
I too tried all combinations of those under nvidia-settings, also with no luck.

'Aspect Ratio Scaled' just puts garbage on my screen as well, which is bothersome to say the least.

Disabling compiz for me has no effect.

---

### Post by alexandrius on 2010-08-14
**El Lance-O** Why do you use that crappy avatar?

---

