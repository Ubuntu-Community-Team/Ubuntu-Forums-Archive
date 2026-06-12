---
title: "Wow color depth reset"
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by ArtificialSynapse on 2007-04-17
WOW runs basically flawlessly with the exception of two little things which forces me to run it in a smaller window : 

Every time I change the color depth from 24 -> 16 in game *AND* in the config.wtf file, it reverts back to 24 color depth after restart. 

AND I get this error, specifically when I go to change the color depth in the menu in game, so I assume they're related :

err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0

Thanks for your help : )

---

### Post by hikaricore on 2007-04-17
In my experience WoW has always done this, even in windows.

It refuses to stay in 16 bit colour.

Anyone feel free to chime in if I'm incorrect, but I've even made the config.wtf file read only to no avail.

---

### Post by ArtificialSynapse on 2007-04-17
> **hikaricore said:**
> In my experience WoW has always done this, even in windows.

It refuses to stay in 16 bit colour.

Anyone feel free to chime in if I'm incorrect, but I've even made the config.wtf file read only to no avail.

Yes I tried that exact same thing! No luck indeed, I imagine WoW builds a file separately somewhere.. I wonder where though. . . .hmmmm

Any ideas about the other error? Because that's what wine pulls when I try to change the depth...

---

### Post by ArtificialSynapse on 2007-04-18
Bump :o

---

### Post by MurnShaw on 2007-04-18
I remember reading at the AMD website that some ATI video cards don't support less than 24 bit depth, just as my 9800. Perhaps that's why?

---

### Post by Ferrat on 2007-04-18
ATi does support 16bit but needs to fool it self that it is 24bit or something like that and WoW that is 24bit missinterpit the feedback and revert to 24bit or something like that, I think in Windows atleast if you set your desktop to 16bit the setting stays

---

### Post by ArtificialSynapse on 2007-04-19
Yup, I've got nvidia anyways, so I suppose I can just make an alternative xorg.conf that runs in 16 bit huh?

---

