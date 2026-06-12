---
title: "[SOLVED] no caps or transparency"
date: 2008-12-05
forum: General Help
---

### Post by cjdaweasel on 2008-12-05
Been looking through the forums for a bit as well as google and I can't find anything that fits my issue.

I upgraded from hardy to intrepid today. Now everything works fine, but I get no cube caps in compiz and I can't make the desktop transparent. Moving the transparency slider in Compiz config and nothing happens. However, other things, like the skydome can be changed.

The only thing I have done thus far to attempt to remedy this is to uninstall and reinstall compiz, compizconfig, and nautilus. This has failed.

I've included screenshots of what the desktop looks like and my current compiz settings.

---

### Post by Wartender on 2008-12-05
are you sure the size is ok? because if it's too big or too small compiz won't display it (i'm not sure what the limit sizes are) try different images and see what happpens

---

### Post by cjdaweasel on 2008-12-05
It worked just prior to installing intrepid. The same pictures, caps and everything. The cube won't change transparency at all, regardless of the picture. Usually I don't have any background, its just transparent.

---

### Post by JECHO on 2008-12-06
> **cjdaweasel said:**
> Been looking through the forums for a bit as well as google and I can't find anything that fits my issue.

I upgraded from hardy to intrepid today. Now everything works fine, but I get no cube caps in compiz and I can't make the desktop transparent. Moving the transparency slider in Compiz config and nothing happens. However, other things, like the skydome can be changed.

The only thing I have done thus far to attempt to remedy this is to uninstall and reinstall compiz, compizconfig, and nautilus. This has failed.

I've included screen shots of what the desktop looks like and my current compiz settings.




ok i am pretty sure i can solve your problem...

when you upgraded to Intrepid you upgraded compiz as well (by default). when you did this you installed new plug ins like "cube reflection and deformation", "wallpaper", etc...

when using compiz on ubuntu 8.10 the effects are managed slightly differently. If you want transparency in the cube and cube caps you must check "Cube reflection and deformation" as well as "Rotate Cube" and "Desktop Cube". ("Cube reflection and Deformation" is located in the Effects section of CCSM.)

...From now on if you want to change the cube caps you must use the Cube Caps option inside of the "Cube reflection and deformation", rather than in the "desktop cube" area. (see attached image)

Hope that helped!

---

### Post by cjdaweasel on 2008-12-06
> **JECHO said:**
> ok i am pretty sure i can solve your problem...

when you upgraded to Intrepid you upgraded compiz as well (by default). when you did this you installed new plug ins like "cube reflection and deformation", "wallpaper", etc...

when using compiz on ubuntu 8.10 the effects are managed slightly differently. If you want transparency in the cube and cube caps you must check "Cube reflection and deformation" as well as "Rotate Cube" and "Desktop Cube". ("Cube reflection and Deformation" is located in the Effects section of CCSM.)

...From now on if you want to change the cube caps you must use the Cube Caps option inside of the "Cube reflection and deformation", rather than in the "desktop cube" area. (see attached image)

Hope that helped!

Excellent. This got my caps back (though they're all stretched out, but I'm not hard to please). HOWEVER, my cube still isn't transparent, even though my caps are. I checked in gconf-editor and nautilus isn't showing the desktop, but compiz isn't making my desktop transparent. How do I make my desktop transparent so I can see what is going on on other desktops?

---

### Post by cjdaweasel on 2008-12-06
> **cjdaweasel said:**
> Excellent. This got my caps back (though they're all stretched out, but I'm not hard to please). HOWEVER, my cube still isn't transparent, even though my caps are. I checked in gconf-editor and nautilus isn't showing the desktop, but compiz isn't making my desktop transparent. How do I make my desktop transparent so I can see what is going on on other desktops?

Nevermind I figured out what I did. Apparently I now have to enable the "Wallpaper" option in CompizConfig. That's new to me :D

In any case thanks for all your help! This one is solved and I have my old desktop back.

---

### Post by JECHO on 2008-12-06
> **cjdaweasel said:**
> Nevermind I figured out what I did. Apparently I now have to enable the "Wallpaper" option in CompizConfig. That's new to me :D

In any case thanks for all your help! This one is solved and I have my old desktop back.

woohoo! glad i could help :)

---

