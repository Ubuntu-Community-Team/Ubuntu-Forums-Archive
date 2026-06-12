---
title: "Morrowind on Ubuntu via Cedega"
date: 2008-02-23
forum: Gaming &amp; Leisure
---

### Post by ChaoticVengeance on 2008-02-23
As an avid gamer, perhaps the only thing about windows I miss is the unfettered ability to run my games, in this case TES III: Morrowind (game of the year edition).  I've tried running it with wine and it runs, albeit very slowly to the point of being unplayable.  I decided to try Cedega, having heard it runs games better than wine.  The problem comes when I try to install the game itself.  Cedega has a very straightforward interface, but I'm unsure where the problem is.  Every time I attempt to install it, the window pops up that says the installshield is preparing, and a loading bar appears.  Once the loading bar reaches 100%, it closes and nothing else happens.  I did note that when I installed Cedega and ran the system test, it failed the OpenGL whatever.  Is this a possible cause for the installation to fail?  I'm not even sure what if it's relevant or what is.

My System:
OS: Ubuntu 7.10 (32-bit version)
Graphics Card: ATI Radeon 9800XT
Processor: Intel 2,8 gHz dual-core

I'm using the fglrx driver with xorg (was required to get Compiz to work).  I suspect my graphics card is the root of all the evil; Had I known I was going to be using linux after I bought the card I would have gotten an nVidia instead.  Any help or pointers in the right direction would be greatly appreciated.  Thanks.

---

### Post by NightwishFan on 2008-02-23
I am sort of surprised it worked so poorly.

The (seemingly unavoidable) issues:

Disable the music. The music refuses to run. You cannot see your avatar in the inventory, but you can equip and 3rd person just fine. The pixel shading renders water glitchy. Other than that I have found nothing however I did not play more than a few times.

If the problem is hardware I cannot help you much. Run this in a terminal, and tell me the output.

glxgears

---

### Post by Perfect Storm on 2008-02-23
> Graphics Card: ATI Radeon 9800XT

The sinner.
Also There's alot of trouble if you using ATI/Intel cards with Cedega.

---

### Post by ChaoticVengeance on 2008-02-23
craig@system42:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
27952 frames in 5.0 seconds = 5562.312 FPS
etc...

I'll try some more after I get home from work.

---

### Post by ChaoticVengeance on 2008-02-28
*bump*

I'm still lost...

---

### Post by owbizi on 2008-02-29
I'm also trying to run (and play, of course, hah) Morrowind on Ubuntu, but I can't even INSTALL the game... wine bad format exe error, it says.

---

