---
title: "Awful Compiz Fusion Tearing"
date: 2007-07-06
forum: Desktop Effects &amp; Customization
---

### Post by TheMono on 2007-07-06
Alright - compiz fusion works perfectly, totally stable, etc - I even like the name.

My only problem is it tears something awful. I'm using a 7600GS on a Core2Duo, compiled with the makefusiondebs script on AMD64, so there is plenty of power for compiz to run, and I get well over 200fps on a normal desktop. If I play a movie, or turn the cube though, it tears awfully.

Using Kwin, videos play perfectly on my DVI monitor (Oh, I am using Nvidia Twinview), however they don't using any composite enabled WM, Beryl included.

I start compiz using the wrapper script written by Trevino, and the line used is "compiz --replace --indirect-rendering; emerald --replace &"

Any tips to avoid this tearing?

---

### Post by ChadMC on 2007-07-06
Maybe try messing with the compiz refresh rate?
CompizConfig Settings Manager >> General Options >> Display Settings

---

### Post by TheMono on 2007-07-06
Tried it. So far I've tried with and without Vblank, with lots of different refresh rates, turning on and off refresh rate detection, so on... I can't figure out how to fix it.

---

### Post by psyopper on 2007-07-06
Take out the indirect-rendering argument. 

Indirect rendering bypasses portions of the nVidia memory limitations (black windows while running Compiz on an nVidia card). If you have 256 meg of memory or better you will not need this argument. This argument (among other things) kills mip-mapping and causes visual tearing - what they refer to as "a loss of image quality to increase performance"

OK, it's not really a quote, but it might be. Seriously though, --indirect-rendering only helps if you have the black windows bug. Take it out and your problems will go away.

---

### Post by TheMono on 2007-07-07
Yes, I should have mentioned, I have tried with --indirect-rendering, with --direct-rendering and with no argument, and there is still the same problem.

---

### Post by Vaun on 2007-07-07
Install fusion-icon from git and set it to loose binding.  Refresh rate at 200 and sync to vblank on in General Options.  You'll get ridiculousy smooth and clear wobbly windows, rotate cube, etc.  However, transparent cube will slow you down a bit with various plugins enabled (cube reflection, 3D windows).  You can have one or the other at the sacrifice of performance and quality.  7600 GS 512 RAM and it runs very nice.

---

### Post by TheMono on 2007-07-08
You must have the same card as me, the 7600GS 512MB. I've tried your suggestion, I'm now starting it with the --loose-binding option, and with the 200 refresh rate and vblank sync enabled.

It did help with wobbly windows tearing, but isn't working for videos, which are still happily tearing away. Thanks for the help though.

---

### Post by TheMono on 2007-07-08
Ah-ha! If I enable the unredirect fullscreen windows option, it helps a lot with fullscreen video tearing, but it still isn't as good as I get under Kwin.

[EDIT: Actually, not, that didn't help at all.]

---

