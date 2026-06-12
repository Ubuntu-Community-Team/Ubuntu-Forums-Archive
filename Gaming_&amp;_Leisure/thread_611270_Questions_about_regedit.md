---
title: "Questions about regedit"
date: 2007-11-12
forum: Gaming &amp; Leisure
---

### Post by zami on 2007-11-12
I'm looking at my registry (regedit), and I'm looking at the "Useful Registry Keys" page over at WINE-Wiki ( [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) ).  And I'm noticing quite a disparity between the two!

For example, the page above lists the key "Alsa Driver", and has six strings defined for that key.  I have no "Alsa Driver" key.

1.
Should I add all these keys?  Or should I just add the keys as specified for specific games? (For example I added a few Direct3D keys to play LOTRO as specified at WineHQ - it's running okay... not great but okay.)

2.
For yes/no values, do I put in "yes" or "y" (or a "no" or a "n" of course)?  I see examples of both used and I don't know if it really makes a difference, or if these are just writers preference or even typos.  

3.
What if I don't know the value?  Such as "UseDirectHW : When set to y, direct hardware access is used (can prevent buffer underruns in some cases)".  I have no idea what the answer to this is - do I add the key and leave the value blank? Not add the key?

Thanks for any advice!

-zami

---

### Post by cogadh on 2007-11-12
[list=1]
[*]None of the keys listed on the "Useful Registry Keys" page exist by default, you need to create them if you are going to use them. Only create the ones you need to use, otherwise they are not required and shouldn't be used.

[*]You should put exactly what is indicated in the description of the key, i.e., if it says set the key to "Y" or "N", then use "Y" or "N" and not "yes" or "no". 

[*]If you leave a key blank, then it won't do anything, as if the key does not even exist. In the case of the "UseDirectHW" key, setting it to "Y" means that Wine will use direct hardware access to your sound card (which can sometimes prevent buffer underruns), setting it to "N" means it will not, which is the same as Wine's default settings. However, unless you are having a problem with buffer underruns, don't bother with it.
[/list]

Basically, those keys are features or functions that are not accessible through the normal winecfg application. At some point in Wine's future development, they may be added to it or may just be eliminated as the features they affect become part of the base Wine. For example, the "VideoMemorySize" key will be eliminated once the actual VRAM detection functions of Wine are completed and work. This recently happened with the "UseGLSL" key. The current version of Wine (0.9.49) actually uses GLSL (OpenGL Shader Language) as the default shader, while Wine versions prior to 0.9.49 used ARB shaders.

For most applications run through Wine, you won't need to mess with the registry keys at all. Some apps do require the fine tuning that they offer, but as Wine matures, there are fewer and fewer apps that do.

One thing you need to remember when you use any registry edits; if you upgrade Wine to a newer version, you need to run "wineprefixcreate" after the upgrade to re-register all the edits you have made.

---

### Post by zami on 2007-11-12
Cogadh,
Thank you, thank you, thank you!

You answered all my questions perfectly!  And greatly simplified my plans for the evening... instead of mucking around in the registry I plan to get right to gaming.

Thanks!

-zami

---

