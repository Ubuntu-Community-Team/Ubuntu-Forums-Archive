---
title: "Compiz + Open GL = Bad Graphics"
date: 2008-03-24
forum: Gaming &amp; Leisure
---

### Post by Ttech on 2008-03-24
I'm not sure but when I enable Compiz and try to use any graphics related thing,  Google Earth,  Wine,  Music Virtualizations,  Screens-aver, they end up choppy, and have random flashing of different icons and such. They also lag a lot and some times even crash the system.  However, my main issue is the flashing,  which only shows up when Compiz is enabled.

---

### Post by talsemgeest on 2008-03-24
What graphics drivers are you using?

---

### Post by grossaffe on 2008-03-24
> **talsemgeest said:**
> What graphics drivers are you using?

yeah, what card/drivers are you using?

---

### Post by bhavi on 2008-03-24
bump!

---

### Post by forrestcupp on 2008-03-24
It's probably because you are using an ATI card with the proprietary drivers.  It's a known issue that isn't going to be fixed any time soon.  The devs say they would have to reprogram the whole structure to fix it, so it seems that they are just waiting on Xorg to fix it at that level.

Your only option is to either turn Compiz off whenever you do anything opengl, or buy an nvidia card.

---

### Post by Melcar on 2008-03-24
> **forrestcupp said:**
> It's probably because you are using an ATI card with the proprietary drivers...  



It's not the drivers.  It's how X handles Composition.  Every card/driver does it, except for nvidia when configured correctly.  DRI2 (when it comes out) will be addressing this issue.

---

### Post by forrestcupp on 2008-03-24
> **Melcar said:**
> It's not the drivers.  It's how X handles Composition.  Every card/driver does it, except for nvidia when configured correctly.  DRI2 (when it comes out) will be addressing this issue.

That's basically what I was saying in different words.  It is possible to have drivers that don't have that problem by including a hacked GLX.  That's what nvidia did.  ATI doesn't want to deal with it, so they're waiting on Xorg.  We'll see how long that takes.

So for now, we either turn off Compiz, or go with nvidia, who did care enough to do something about it.

---

### Post by DJ_Peng on 2008-03-24
Keep in mind that you may sufficient RAM/video RAM to be able to use some of these programs simultaneously. Google Earth will suck up a ton of resources all by itself due to the nature of the program, and some screensavers may need more RAM than you're throwing at it. I've never had weird icons or flashing but I know if I want to run GE I need to kill Compiz temporarily (same with SecondLife) and some of the screensavers jump on my system with under a gig of RAM and an older video card with maybe 128 MB of video RAM.

---

### Post by w4rh4wk on 2011-05-07
i encountered the same issue.

i recently installed ubuntu 11.04 on my laptop (acer aspire 5739)
the GPU is a GeForce GT240M and i installed the latest driver from the nvidia website (linux 32 bit)

i tried out opengl by using glxgears... problem is, FPS is around 4200 but the window and everything lags.

the problem is compiz! when i deactive compiz and use metacity the fps drops to 2100 but the window and everything runs smooth.

---

