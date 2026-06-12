---
title: "Did I find the solution to choppy games in Ubuntu?"
date: 2007-01-07
forum: Gaming &amp; Leisure
---

### Post by tocleora on 2007-01-07
I realize this is just one instance but maybe if it's not an overall solution it will start thoughts and conversations that may help solve this problem.  I'm assuming the problem isn't resolved globally among all games as when I submitted request for assistance with this a few times no one responded.  If this is resolved globally please provide information. :)  If anything maybe this will help people with Sauerbraten.

I installed Sauerbraten this morning.  As with a lot of games I've played on Ubuntu, it was slow and choppy and I was frustrated, as one of my friends got it working in Windows and I was sure he'd rub it in that it didn't work for me.  I decided to review the manual and found this:

> When used alone, "-f" forces the renderpath to the old fixed function pipeline (no shaders), otherwise it sets the shader precision to N (lower = faster). 0 disables shaders, 1 uses the fastest/lowest precision the OpenGL driver offers, 2 is the default precision, and 3 is the nicest/slowest precision.

So I decide to try this:

```
sauerbraten_unix -f0
```

And it worked perfectly.  Any thoughts, comments, additional information?

---

### Post by aidanr on 2007-01-07
no you found a solution for a choppy game in ubuntu on (i'm guessing) a low end video card

turning off shaders will naturally increase framerate at the cost of visual quality

what are your specs anyway, i run sauerbraten on a 2.8 p4, 128mb 6800 and 1 gig ram and it runs fantastically with everything turned on

---

### Post by Biggus on 2007-01-07
> And it worked perfectly. Any thoughts, comments, additional information?

Yeah, great stuff.

If yer graphics card is none to clever with shaders, then this little fix seems to be just the job for this game.

---

### Post by tocleora on 2007-01-07
I have a Fujitsu laptop with an Intel Graphics Media Accelerator 900 graphics card.   I would guess not the best for gaming but it runs Halo in Windows perfectly... Does that help and/or mean anything?

---

### Post by Biggus on 2007-01-07
I'm not sure (I am actually almost entirely certain, but I've been made a fool of before on internet forums) (just as I typed that there, the word 'internet' is highlighted by my Firefox browser as not being spelled correctly - now I'm really in danger of losing it) but I think that Halo would probably use DirectX instead of OpenGL, so no joy I'm afraid.

---

### Post by tocleora on 2007-01-07
Apparently my graphics card will handle up to 128MB and is somehow dynamic based on the amount the software I'm running needs.  Something tells me it's "dynamic" because of something in Windows (just like my sound automatically moves from my internal speakers to my headphone jack when I plug in headphones "dynamically" where in Ubuntu they show up as two separate outputs), so I put a value in my xorg.conf "VideoRam 131072" and it does seem to be a little less choppy, but still choppy none the less.    I have a hard time believing it's 100% my graphics card when Halo will run (even if it does run using DirectX instead of OpenGL) which would leave video drivers or OpenGL compatibility, or just not configured correctly by me.  I always assume the latter however as my graphics card works too well overall to be driver related and OpenGL works for many many other people.  If anyone has any other thoughts or ideas I'd love to hear them, otherwise I'll just keep tweaking and testing. :)

---

### Post by Frem on 2007-01-09
If you have an ATi card, it is entirely possible, even likely, that you'll have worse performance in OpenGL then DirectX. For one thing, ATi's Linux driver is pretty pathetic. For another, some cards (my Radeon Xpress 200m included) had a firmware bug that offloaded a bunch of OpenGL features onto the CPU instead of handling them on the card like it was supposed to. As a result, many games are completely unplayable when running in OpenGL mode in Windows, even though they run fine using DirectX.

---

