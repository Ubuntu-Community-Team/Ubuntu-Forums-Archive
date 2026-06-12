---
title: "Beryl movement choppiness (slight return)"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by klato on 2007-04-29
Hi all,

I'm using Beryl 0.2.0 from the repos, and all is well pretty much.  I've got an nVidia Geforce Go 7300 graphics card in my lappy.

The only issue I've got is that whenever I move a window and do some animations, there is a bit of choppiness at first.  For example, I'll have the gaim buddy list open, and if I go to move it, it will stutter around for about 2 seconds and then it will be very smooth.  I've tried messing around with the Sync and Refresh rate options in beryl settings manager, but it didn't have much effect.  (although I must say Beryl looks way better for me if Sync to vblank is enabled...too much tearing otherwise).

Does anyone know what's up?

Thanks!

---

### Post by lithium on 2007-04-29
If you drag and hold a window for longer than the stuttering happens, will it move smoth from there on, or will it return to stuttering after a short while? Because this is what I see here...

---

### Post by klato on 2007-04-29
Yep, I'll drag the window, it'll stutter for a second, and then it will move smoothly.  A couple minutes later I'll drag that same window again, the same thing happens.

---

### Post by lithium on 2007-04-29
Just what I get!

I'm using compiz, so we can rule out compiz/beryl as the problem... What driver version are you using? The nvidia-glx-new one?

---

### Post by klato on 2007-04-29
Cool...maybe we can get to the bottom of it.  According to synaptic package manager, I've got nvidia-glx 1.0.8776 installed.

---

### Post by lithium on 2007-04-30
nvidia-glx 1.0.8776? That doesn't even show up here... I have the nvidia-glx version 1,0.9631 installed. Are you using Feisty? And, are you using XGL? I was under the impression that I don't use XGL here, certainly I didn't start it myself...

---

### Post by lithium on 2007-04-30
Ha, think I found the problem!

Please aktivate compiz or beryl and then do:

killall evolution-data-server-2.10

I don't know what's wrong but this really fixes the problem on my sis' PC! I then deactivated the Evolution Alarm thing from the Sessions capplet, now everything works fine.

Can you confirm? Evolution bug?

---

### Post by klato on 2007-05-01
wow that's crazy...i disabled the evolution alarm in sessions and beryl is running smoother than ever now!

how on earth did you figure it out?

cheers

:popcorn:

---

### Post by Muppeteer on 2007-05-01
The way i get beryl to run smoother is turn off the vsync and detect refresh rate...then set the refresh rate to 200 :)

---

### Post by lithium on 2007-05-01
> **klato said:**
> wow that's crazy...i disabled the evolution alarm in sessions and beryl is running smoother than ever now!

how on earth did you figure it out?

cheers

:popcorn:


I did what I should have done in the beginning: take a look at "top". If you see the evolutiopn process jump to 50-60% cpu something is going very wrong :lolflag: 

Anyway, time to report a bug I guess.

---

### Post by klato on 2007-05-16
I upgraded to Feisty and it looks like this choppiness stuff is back.  Tried killing all evolution related  stuff, unchecked detect refresh, maxed out refresh in beryl-settings, added triple buffer to xorg, but i still get lag sometimes during movement and animations :(

---

