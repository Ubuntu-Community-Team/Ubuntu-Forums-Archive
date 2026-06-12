---
title: "No text in GL games"
date: 2007-11-05
forum: Gaming &amp; Leisure
---

### Post by My Lost Shadow on 2007-11-05
I have a problem. On all games that use openGL the text is missing (actually it is just a white box covering it). I don't know what to do.

My system is an Inspiron 6400 from Dell with an Intel Core2Duo at 2Ghz, 2GB RAM and an Ati Mobility X1400.

There are two attached screenshots, one with the text (or the way it shows) and one with the output of Eternal Lands.

---

### Post by khughitt on 2007-11-05
A couple thoughts come to mind:

1. Have you tried using different fonts in the font-settings manager?

2. In your theme settings, are any of the text types using white as a background color? Have you tried changing that?

---

### Post by My Lost Shadow on 2007-11-05
I've just tried using different fonts and nothing changed. Also, none of the text types I use have white background color.

I still think that the problem is openGL related.

---

### Post by khughitt on 2007-11-05
Are you using the restricted drivers manager driver for your ATI card?

---

### Post by My Lost Shadow on 2007-11-05
Yes, I'm using the restricted drivers manager driver for my video card along with the repository driver. I found the latest Ati driver release to be disappointing.

---

### Post by reagentz on 2007-11-05
I have the same issue running World of Warcraft in OpenGL, the cursor will show up in the login box, but no words will type in, when I close out to the desktop and look at the terminal window I used to launch the game all the text I was trying to type in is all typed out in there.

I gave up using OpenGL and just used D3D which is semi-lame. I think OpenGL looks/performs better.


Edit: And yes I agree with you it is OpenGL related it has nothing to do with compiz, emerald, fonts in themes, desktop background colors etc. and like you also I'm running the absolute latest nVidia drivers.

I'm also running 2x xFx 7800 GT SLi cards, Asus A8N mobo, Athlon 64bit FX-55 CPU, 4gb OCZ RAM.

---

### Post by WinterHico on 2009-10-23
I'm having this problem too in Eternal Lands.

Ubuntu 64 9.04

I found a post:

[http://forums.gentoo.org/viewtopic-t-501397-start-0.html](http://forums.gentoo.org/viewtopic-t-501397-start-0.html)

which notes that XGL may be the problem.  I'm at work and cannot try it now, but I will as soon as I get the chance.

[Edit]
Another thread:
[http://ubuntuforums.org/archive/index.php/t-304316.html](http://ubuntuforums.org/archive/index.php/t-304316.html)

More info:
I have two machines both running the same OS.  One has an nVidia 8600GT card and the other is running nVidia 6300 on the motherboard.  The machine with the 8600GT runs just fine with everything running (XGL, Compiz, ...).  The machine with the on-board 6300 is the one with the problem.  I tried turning off Compiz but that didn't help.  I will update again when I disable XGL.

Final status:
Disabling XGL did not help in my situation.  I ended up updating to Ubuntu 9.10, Karmic, and it still did not work.  Finally, I INSTALLED 9.10 fresh (not an update).  Once I did this, I no longer had the problem.  Some times when updating to a new version of Ubuntu, some settings or what-not from the prior version linger and can have negative effects.  More than once I have run into this sort of thing, so now I don't "update" - instead, I download the new version, burn it and install over the prior version.

---

