---
title: "Enable or Disable DGA"
date: 2005-08-28
forum: Gaming &amp; Leisure
---

### Post by fragmental on 2005-08-28
I've never really understood whether I wanted DGA enabled or not.  I am of course, thinking about games here.  Does the mouse work better with it enabled in some games?  Does it really matter for most games?

Specifically, does it matter with ut2004 or Quake3?

I have a radeon card and I noticed recently that the DGA extension works with the drivers now so I was curious because I've never really seen anything about how DGA affects games.

---

### Post by endy on 2005-08-29
I use DGA with Quake 3, ET etc... I prefer the mouse movement like that as it seems smoother and perhaps more direct :)

---

### Post by fragmental on 2005-08-29
[QUOTE=endy]I use DGA with Quake 3, ET etc... I prefer the mouse movement like that as it seems smoother and perhaps more direct :)[/QUOTE]
 Is Quake 3 mouse movement really smoother or does it just seem that way?
Do you play ut2004?

When I set my computer to DGA, Unreal Tournament 2004 will run with a black border if it's not set to the desktop resolution, and my computer can't handle ut2004 at 1280x1024.  Does anyone know why or how I can fix it?

---

### Post by endy on 2005-08-29
Well I play ET more and I know that until the 2.60 release there was a problem where you couldn't totally get rid of mouse acceleration. Now, for ET at least, you can set "in_dgamouse 2" which fixes and it makes sure there is no mouse acceleration. That's a big reason why I use it in ET but I don't know if this was ever an issue on Quake 3 and I don't play UT but I bet DGA is good on that :)

---

### Post by fragmental on 2005-08-30
[QUOTE=endy]Well I play ET more and I know that until the 2.60 release there was a problem where you couldn't totally get rid of mouse acceleration. Now, for ET at least, you can set "in_dgamouse 2" which fixes and it makes sure there is no mouse acceleration. That's a big reason why I use it in ET but I don't know if this was ever an issue on Quake 3 and I don't play UT but I bet DGA is good on that :)[/QUOTE]

By mouse acceleration, you mean DGA?  So, you had DGA enabled in ET, because ET needed it and therefore you couldn't get rid of it? 

I said Quake 3 and UT because pretty much ever game that requires high performance on Linux uses either the quake or unreal engine.

I would proabbly leave DGA enabled, but as I mentioned above, there's a weird issue with ut2004 where it will keep the desktop resolution and make a border around it.  There might be a way to fix that, but I don't know what it is.

Does DGA hurt or help FPS performance or does it not matter?  Maybe I should try a different forum?

---

### Post by endy on 2005-08-30
The problem with mouse acceleration in ET was an error in the ET code IIRC, and now it properly handles DGA mouse input without any acceleration. AFAIK, DGA and mouse acceleration are seperate. I can't find any references on google but I'm pretty sure DGA allows for more direct input and if working it should be a good thing.

BTW, I think it may be necessary to have the following in your xorg.conf:
```
    SubSection  "extmod"
      Option    "xfree86-dga"
    EndSubSection
```
In the "Modules" section at the top as by default it set to be omitted, perhaps this could help UT?

Also AFAIK in id games DGA is only used for mouse input so it shouldn't affect FPS :)

---

