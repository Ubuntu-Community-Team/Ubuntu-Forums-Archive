---
title: "Diablo2 cant scale image"
date: 2008-03-26
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2008-03-26
Im trying to play diablo2 + LOD on a widescreen monitor.  So far, I have two choices, play in a small window on the screen, or streach the image fullscreen where everything is distorted.

How can I set it up to scale the image so that I get black bars on the sides of the game?  I have heard image scaling option in the nvidia-settings, but I cant find them there.

By the way, im running kubuntu gutsy with the restricted drivers from the repo's, and have a widescreen monitor connected through the vga port if any of this helps.

---

### Post by disturbedite on 2008-03-26
impossible.
diablo 2/lod is so old it is hardcoded to run in 640x480 or 800x600.  (as you might be able to tell, those resolutions do not have widescreen aspect ratios).  it is not possible to force it to run at any other resolutions/aspect ratios with wine.

---

### Post by basketcase421 on 2008-03-26
Have you tried resizing those resolutions in your monitor's controls?  I used to do that with games I wanted in widescreen on my regular aspect CRT.  Set the resolution in game, and then use the picture "squeezing/expanding" options on the monitor.

---

### Post by Naegling23 on 2008-03-26
Well, I know that the game wont run in widescreen.  What I am asking is how do I set the game up to run with the scaling option so that the black bars are on the side of the screen.

I know this is not really a gaming question, but this section of the forum is best at answering these sorts of questions.

A google search tells me that I need to go into nvidia-settings and change the scaling options.  The only problem is that I do not see these options, unless they are called something different, or I am looking in the wrong place.  I was hoping that someone would be able to help me out.  I was going to try to manually insert:
Option "FlatPanelProperties" "Scaling = aspect-scaled"
into the devices section of my xorg.conf file to see if that works.  Im unsure if I am on the right track to being able to fix it or not.  Im planning on trying it when I get home from work, just wondering if anyone has a better, or clearer explanation that could help.

One other thing, at the end of last night, I realized that in my display settings, my monitor was set up as 4:3, I had manually added widescreen resolutions to xorg.  I switched it to widescreen which required a reload of xorg, but I went to bed before I could check to see what it did.  Could this be the culprit(I doubt it though)?

---

### Post by basketcase421 on 2008-03-26
Did you try using the horizontal "squish" control on your monitor?  (I don't know what it is really called...).  The 4:3 image (800x600) is stretched across your 16:9 screen.  So, to get black bars on the sides, you could squish the image on your actual monitor controls.  That is assuming your monitor has this ability.  I don't know if they all do... or maybe LCDs don't have that option.  If you can do this, and assuming you don't ever use 800x600 for any other things, it should affect your normal desktop resolution.  Most monitors have different settings "remembered" for each resolution it uses (at least mine does...)

Good luck!

---

### Post by Naegling23 on 2008-03-26
Its an option, I'll look into it.  It seems more like a sort of work around though, while Im trying to just fix the problem at hand instead.

---

