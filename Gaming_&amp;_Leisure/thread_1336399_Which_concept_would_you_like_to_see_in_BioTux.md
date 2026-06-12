---
title: "Which concept would you like to see in BioTux?"
date: 2009-11-24
forum: Gaming &amp; Leisure
---

### Post by NinjaNumberNine on 2009-11-24
Sorry for the horrid art, but here's a few different costume concepts for "MegaTux" in the game mentioned in my sig- I only had time to draw a few of those mentioned in the poll.
Thanks! :D

---

### Post by NinjaNumberNine on 2009-11-24
:D Bump :D

---

### Post by NinjaNumberNine on 2009-11-26
*in shock*  not one out of 52 linux users can suggest a single one? Wow, am I the only Tux fan here? ;)

---

### Post by pyrael on 2009-12-04
I think just a huge Tux would do perfect. maybe a bit more muscular but no special attire.

---

### Post by NinjaNumberNine on 2009-12-04
Hadn't thought of that. :D
I actually like that idea!

I'll crank out a few images in a day or so of the new "MegaMuscularTux" (LOL)

But seriously, good idea. I can't wait to start drawing.


Thanks,


NinjaNumberNine

---

### Post by hessiess on 2009-12-05
There is a fully rigged and animatable Tux model [here](http://www.blendernation.com/links/tux-rig/), Feel free to use it if you want.

---

### Post by NinjaNumberNine on 2009-12-06
Thanks, hessiess. I seem to remember meeting before...
Oh well. I downloaded the blender file and started the very long process of rendering a frame (I just have a GB of ram and a no-good graphics card (intel-based)) and as it printed it out, I noticed a striking concept: Tux here is glossy, but-

-MegaMario is glossy too! I wondered what the similarity was.. :D

[IMG]http://fc06.deviantart.net/fs45/f/2009/094/9/2/The_Mega_Mario_Network_by_LBDNytetrayn.jpg[/IMG]
(yes that's actually what he looks like in the game)

I love the fact that you can rotate his arms and legs- that will save lots of work on the animation.


The problem:

I cannot possibly do all the rendering on my computer- not with the screen fps being about 0.001... ;)


So if anyone out there has a better graphics card or more ram than I do, I would really appreciate it if you would capture some frames of tux in a looping walk animation from the side view.


Thank you, and remember, your help is VERY much needed!


As always,

NinjaNumberNine

---

### Post by hessiess on 2009-12-07
> **NinjaNumberNine said:**
> 
I downloaded the blender file and started the very long process of rendering a frame (I just have a GB of ram and a no-good graphics card (intel-based)) and as it printed it out, I noticed a striking concept: Tux here is glossy, but-

...

I love the fact that you can rotate his arms and legs- that will save lots of work on the animation.


The problem:

I cannot possibly do all the rendering on my computer- not with the screen fps being about 0.001... ;)

If you are referring to the OpenGL rendering (the 3d view port) you can try reducing the `Levels' parameter in the sub serf modifier. [see here](http://www.blender.org/development/release-logs/blender-240/modifier-system/)
If you are referring to the blender internal rendering being slow, thats because the blend set to render in 75% HD by default. Blender internal is a software renderer and is mainly limited by CPU, not GPU performance. you can see the resolution settings in the right of the first image on [this](http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/Render_Settings) page. Setting the output resolution to around 256 or 512^2 would be appropriate for most 2D games,and reduces the render time per frame to about 10 seconds.

See [here](http://wiki.blender.org/index.php/Doc:Tutorials/Animation/BSoD/Character_Animation/Setting_up) for a basic intro to animating in Blender.

---

### Post by NinjaNumberNine on 2009-12-11
> **hessiess said:**
> If you are referring to the OpenGL rendering (the 3d view port) you can try reducing the `Levels' parameter in the sub serf modifier. [see here]("http://www.blender.org/development/release-logs/blender-240/modifier-system/")
If you are referring to the blender internal rendering being slow, thats because the blend set to render in 75% HD by default. Blender internal is a software renderer and is mainly limited by CPU, not GPU performance. you can see the resolution settings in the right of the first image on [this]("http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/Render_Settings") page. Setting the output resolution to around 256 or 512^2 would be appropriate for most 2D games,and reduces the render time per frame to about 10 seconds.

See [here]("http://wiki.blender.org/index.php/Doc:Tutorials/Animation/BSoD/Character_Animation/Setting_up") for a basic intro to animating in Blender.

Thanks again....


I still couldn't get it to render at any decent speed, though- and is there a way to add transparency to the output file?

TTFN,

NinjaNumberNine

---

### Post by hessiess on 2009-12-12
Here is a [Blend file](http://hessiess.com/resources/tux_rig_side.blend) with the camera moved to the side of the character and set to orthographic and the resolution set to 256*256. After pressing f12 to render, it takes 11 seconds to complete on my computer. You can save the rendered frame, with transparency by pressing the f3 key after the render has completed. Or hit the big orange `anim' button to render an animation;)
 
[Here](http://hessiess.com/resources/tuxanim.zip) is a rendered walk cycle(sequence of TGA images) that I made with an older version of the charicter. I have since re-rigged the character and the animation does not work with the new rig.

---

### Post by NinjaNumberNine on 2009-12-12
I tried the new file, and to my suprise and gratification, it rendered in about 3 seconds! Problem is...    :D

Now the rendered file leaves out his eyes for some reason...


I'm sure it's something I'm doing wrong- thanks so much for all you've done to help. =D>

Really- I was feeling sort of hopeless- no one seemed to volunteer in the art area, and I'm nothing of an artist myself- but when you came and offered that model, that encouraged me a lot- I won't forget it!

I think I can get the eyes to show up somehow anyway, I do love how fast blender renders now (maybe it has something to do with changing over from KDE to Gnome) :D

So thanks for everything,


NinjaNumberNine

---

### Post by NinjaNumberNine on 2009-12-12
Hmm, got it working... I just reloaded the blend file- must have been something I clicked. :D

---

### Post by hessiess on 2009-12-13
You hid layer 2 somehow (probably pressed the 1 key)
[http://wiki.blender.org/index.php/Doc:Manual/3D_interaction/Navigating/Layers](http://wiki.blender.org/index.php/Doc:Manual/3D_interaction/Navigating/Layers)

---

### Post by NinjaNumberNine on 2009-12-13
> **hessiess said:**
> You hid layer 2 somehow (probably pressed the 1 key)
[http://wiki.blender.org/index.php/Doc:Manual/3D_interaction/Navigating/Layers](http://wiki.blender.org/index.php/Doc:Manual/3D_interaction/Navigating/Layers)Oh, that's it. I had remembered that the numbers would switch views but I had forgotten that those were on the num lock keys, not the ones above the letters. :D

Thanks!

---

### Post by ObsequiousNewt on 2012-01-26
Tux with a ninja belt?

---

