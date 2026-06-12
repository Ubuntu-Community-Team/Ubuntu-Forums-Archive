---
title: "Help playing FPS- is 3D acceleration working right?"
date: 2010-04-05
forum: Gaming &amp; Leisure
---

### Post by cbecker78 on 2010-04-05
I am having some serious trouble with getting Sauerbraten to work (in campaign mode), and even TuxRacer is a little laggy...

my computer specs are as follows
```
    **[FONT=&quot]Processor[/FONT]****[FONT=&quot]and Graphics[/FONT]**
  [FONT=&quot]Intel[/FONT][FONT=&quot]® [/FONT][FONT=&quot]Pentium[/FONT][FONT=&quot]® [/FONT][FONT=&quot]processor T4400[/FONT] (dual core)
  [FONT=&quot]2.2GHz, 1MB L2 Cache, 800MHz FSB[/FONT]
  [FONT=&quot]Mobile Intel[/FONT][FONT=&quot]® [/FONT][FONT=&quot]GL40 Express Chipset[/FONT]
  [FONT=&quot]Intel[/FONT][FONT=&quot]® [/FONT][FONT=&quot]Graphics Media Accelerator 4500M with 128MB-1341MB[/FONT]
  [FONT=&quot]dynamically allocated shared graphics memory[/FONT]
  **[FONT=&quot]Memory[/FONT]**
  [FONT=&quot]Configured with 3GB DDR3 800MHz (max 8GB)[/FONT]
  
```when running "glxgears" the average readout is around 2500 frames in 5.0 seconds (averaged over a few minutes).

Should I be able to run games like Sauerbraten, or is this setup simply not good enough?  prboom is pretty snappy, but then, I can run that on my cell phone with windows CE.

Thanks for any input...

---

### Post by SamHowells on 2010-04-05
Hello,
I'm not entirely familiar with that game, but from the screenshots it looks relatively graphical.
Unfortunately your integrated graphics chipset might not cut the mustard, I'll run it on my machine with an 8800GTS and see what sort of frames I get.

Cheers
Sam

---

### Post by disturbed1 on 2010-04-06
From [http://cube.wikispaces.com/Performance+Guide](http://cube.wikispaces.com/Performance+Guide)
> 
If you are using an Intel GMA chipset, then certain player models will be much faster to render than others. Use the "Ogro" player model, which can be selected in the options menu, or you may choose him from the Sauerbraten console by typing /playermodel 2.

Also, if you are using an Intel GMA chipset, turn off stencil shadows by going to the options menu, then under the gfx tab make sure the stencil shadows option is off. You may alternatively shut these off from the Sauerbraten console by typing /dynshadow 0.

Cube2 actually has pretty low specs to *run* the game. You should be able to at least play it with your hardware. _Any_ dedicated graphics would yield better results though. Sadly that's not an option with Notebooks.

---

### Post by cbecker78 on 2010-04-06
I'm not entirely sure still if my graphics are working as they should yet, but thanks for the link and info!  At least I know I "should" be able to make it work.

I will try some of those options over my lunch break and see if the environment will load.

---

### Post by cbecker78 on 2010-04-06
well, no luck. I have only been able to make it past the "loading" screen once after adjusting all the settings and dropping resolution way down.  Even that once there was a horrible lag (movement about every 30 seconds) that I had to kill from another tty.

I noticed that the repo version does not have the option to use player model "orgo" and putting "playermodel 2" into the sauerbraten terminal doesn't recognize the "playermodel 2" command.

thanks for the help, and please let me know if there are any additional thoughts!

---

### Post by cbecker78 on 2010-04-06
-deleted duplicate post-

---

