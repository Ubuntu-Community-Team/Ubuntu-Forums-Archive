---
title: "misssing text"
date: 2006-08-05
forum: Desktop Environments
---

### Post by lifeboat47 on 2006-08-05
just downloaded firefox (latest) and installed theiir flash player (Iread aol news a lot and flash is needed for all content) seems I get the pictures but not getting text to accompany any of the articles in that news item - how do i get the text even though flash installed without any problems???

---

### Post by someusernoob on 2006-08-05
Basicly you have 2 options:

1. Install msttcorefonts. But > this will affect a lot of webpages, they will use the MS fonts in stead of the standard Ubuntu fonts, so things will get ugly if you love the standard fonts.

2. Install gsfonts-x11. This is a dependency of the flash plugin. But... (yeah again) it looks ugly. It is readable, but its just ugly. It also affects some GTK1.0 applications, i.e. the menu of XMMS. It doesnt affect the fonts on webpages like msttcorefonts does.

And i remind there was an issue with one of the 2 not working when you're using xgl/compiz. It is in my post history somewhere.

/EDIT: Aol News isnt the only site btw. Other sites that i know of and dont show fonts without one of the two installed are [www.planet.nl](www.planet.nl) and [www.korn.com](www.korn.com).

/EDIT 2: found my post about the fonts:
[http://ubuntuforums.org/showthread.php?p=1240399#post1240399](http://ubuntuforums.org/showthread.php?p=1240399#post1240399)

---

### Post by lifeboat47 on 2006-08-05
Yikes, Someusernoob !! What a fast and kind reply (and accurate too - what you said acutally WORKS!!!  LOL)  Thanks ever so much    Sail

---

### Post by hanzj on 2006-08-15
sudo aptitude install gsfonts-x11
> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Where's gsfonts-x11?

---

### Post by hanzj on 2006-08-15
I haven't found gsfonts-x11 yet, so in the meantime i installed msttcorefonts. But I still can't see text in flash.

How can this be fixed?

---

### Post by someusernoob on 2006-08-16
Are you using XGL/Compiz?

Otherwise you should be abel to see all the text with msttcorefonts.

What site are you looking on?

And probable you need to enable a(nother) repository for the gsfonts-x11  package. I do not know which one tho.

---

### Post by hanzj on 2006-08-16
I don't know whether I'm using XGL/Compiz.
I'm looking at  litaquatics DOT com

---

### Post by someusernoob on 2006-08-16
If you do not know if you're using XGL/Compiz you're probably not using it.

[It's that 3D eyecandy stuff.]("http://images.google.nl/images?q=xgl%2Fcompiz&ie=UTF-8&oe=UTF-8&client=firefox&rls=org.mozilla:en-US:unofficial&sa=N&tab=wi")

I do not know in which repository gsfonts-x11 is located.

Open Synaptic, click on reload and do a search for gsfonts-x11. If he doesnt find it, click on Settings > Repositories, and check all empty boxes, close that window and reload again (or he will do this automaticly, im not sure). After that search for it again and install it.

---

