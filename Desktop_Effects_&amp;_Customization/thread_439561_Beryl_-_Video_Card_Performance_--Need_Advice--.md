---
title: "Beryl - Video Card Performance --Need Advice--"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by zleilndka on 2007-05-10
I just need to know (if any) which video cards run perfect/near perfect while running Beryl.  My old card runs Beryl, but the frame rates dip pretty low, 15-20ish fps, when scrolling in Firefox and watching video.  My LCD monitor is 1680x1050 in resolution, so that probably has a little bit to do with the sluggish performance.  

Long story short, I just need to know of some video cards that are known to perform well at high resolutions (with video running and effects) and supports all the eye-candy that Beryl provides.

~My current card is a Radeon 7500LE 64mb.  Sorry if this has been posted before.

---

### Post by LollYouSuckZor on 2007-05-10
NVidia. Geforce.

Nothing more to say.
Gamer? Nvidia.
Computer user? Nvidia.
Nvidia.
:)

---

### Post by zleilndka on 2007-05-10
Do "all" nVidia cards run well, or just most of them of them.  I've heard though that some are better than others in running Beryl, I just need one to run Beryl perfectly and minimized the hassle.  Games, I don't really need to worry about them too much.  The games I do play fall towards the low end of the spectrum graphically.

---

### Post by LollYouSuckZor on 2007-05-10
Well then your fine.

I guess I would have to ask, what would you be doing with Beryl?

---

### Post by zleilndka on 2007-05-10
Not too much to tell you the truth (though I do like some of the usability features on Beryl).  Now that graphics cards are getting relatively cheap and my video card is feeling pretty dated, it feels like the right time to upgrade.  So I thought, might as well get one that fully supports Beryl.

~If my video card can't even handle a screen saver smoothly, I know somethings wrong.

---

### Post by Hewure on 2007-05-10
I assume it's PCIe?

7600GS is a good performer for the $, they've come down in price - here anyway - because of the 8xxx series.

---

### Post by zleilndka on 2007-05-10
That's one thing I forgot to mention, no I don't have PCI express.  I only have an 8 x AGP slot, and my old card is PCI video card.

---

### Post by Hewure on 2007-05-10
Same boat as me!!!

Can still get new 76xx series cards for AGP. Or perhaps look for a 2nd hand 6600GT or similar.

There's a cheaper 73xx series, but looking at the Benchmarks on Toms Hardware, you're far better off spending a few extra $ on a 76xx

[http://www23.tomshardware.com/graphics_2007.html](http://www23.tomshardware.com/graphics_2007.html)

I'm saving for a 7600GT, but I game a fair bit.

---

### Post by zleilndka on 2007-05-10
Thanks, for the recommendations, I'll look into those.

---

### Post by hachaboob on 2007-05-11
I have an nVidia 6600GT and had performance issues like video stuttering when web pages were loading. I found this little tip somewhere (can't remember where or I'd link to it and credit them).

Put this into your /etc/profile:

```
export __GL_YIELD="NOTHING"
```

This seemed to help out greatly.

---

### Post by Hewure on 2007-05-11
my 6600GT runs fine.

I installed the latest Drivers using Envy, then Beryl, and it works sweet!

---

### Post by zleilndka on 2007-05-13
> **hachaboob said:**
> I have an nVidia 6600GT and had performance issues like video stuttering when web pages were loading. I found this little tip somewhere (can't remember where or I'd link to it and credit them).

Put this into your /etc/profile:

```
export __GL_YIELD="NOTHING"
```

This seemed to help out greatly.

> **Hewure said:**
> my 6600GT runs fine.

I installed the latest Drivers using Envy, then Beryl, and it works sweet!

So, did you have any problems as hachaboob did with stuttering Hewure?  Or did yours work with no issues?  

I am seriously considering the 6600GT, but I am also considering spending a little extra money to get a 7600GT.  I just have to research about the 7600GT a little more.  Though it seems as though I can't go wrong either way--6600GT or 7600GT.

Also have you (anyone) tried this tweak and if so, did it help on the 6600GT?
[http://liquidweather.net/howto/index.php?id=106](http://liquidweather.net/howto/index.php?id=106)

~I did end up getting a 7600GT and it works great with Compiz Fusion--no stutters, smooth framerate, very few glitches (for some reason the Snow plugin renders solid white squares), and overall a great card.  Thanks for all the help.

---

