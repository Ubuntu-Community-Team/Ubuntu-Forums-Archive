---
title: "New Games will not run"
date: 2008-12-12
forum: Gaming &amp; Leisure
---

### Post by Computer3.14 on 2008-12-12
Ok, I have given up on looking for someone with a similar problem, so I have decided to post:

My problem is that the games that I am trying to play are not working each fails to start up.  For example Frozen Bubble pops up a window and says loading .... the the window closes and nothing happens.  Nexuiz does about the same thing except the screen goes black and pops up their logo... then nothing happens, it goes back to the desktop.  SMC (Secret Maryo Chronicles) flashes up another window and it also closes.

Things that I know:

glxinfo | grep rendering = yes

I have 3D-accelerated proprietary graphics driver for NVIDIA cards (177) Installed.

And my Mobo is a p6n diamond from msi which has a sound blaster x-fi built in so no audio working atm.

I am sorry I can't give you more info, I am still really new and don't even know where to start trouble shooting.



main specs
MB p6n diamond
core 2 duo e8400
geforce 8800 gt
random ram that works 2 gig

---

### Post by Perfect Storm on 2008-12-13
Try start th games through the terminal, this might give you more info what is happening.

---

### Post by Computer3.14 on 2008-12-13
> ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: stream.c: Assertion 's' failed at pulse/stream.c:971, function pa_stream_drain(). Aborting.
Aborted


Fairly common issue, i see others have had the same problem.

Thanks 


(I haven't fixed it yet, hungry, but at least now i know what the problem is.)

---

### Post by Perfect Storm on 2008-12-14
I see you have x-fi sound-cards. If you don't mind and if you have onboard card on your mobo - you can use that instead. 
The x-fi driver aren't great and still beta AFAIK.

---

