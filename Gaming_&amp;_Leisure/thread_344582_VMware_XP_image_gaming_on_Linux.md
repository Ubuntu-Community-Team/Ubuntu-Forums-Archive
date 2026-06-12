---
title: "VMware XP image gaming on Linux"
date: 2007-01-23
forum: Gaming &amp; Leisure
---

### Post by Moodel on 2007-01-23
I'm a fairly big gamer and for obvious reasons I havn't switched to Linux full time yet for that purpose. 
 
I'm not a noob to Linux as I use it at work and at home (when not gaming). 
 
I've a fairly beefy machine with 4Gb of PC2-6400 Corsair running on it. 
 
What I want to know the answer to is would it be possible to run a VMware XP image and then play and run games as though on a native XP machine? 
 
Has anyone tried it and does anyone know what the impact/drawbacks might be? 
 
Any help appreciated

---

### Post by conjur3r on 2007-01-23
Until there is capacity for 3D rendering, you will not be able to play games unless you have them running in software mode.  You will not get hardware accelerated graphics.  However, for games that do not require 3D acceleration, they will run fine particularly on a system with 4GB!

Have you looked at wine and cedega?  Maybe some of the titles you reguarly play have had some previous success running on linux using either of these.

---

### Post by DerHesse on 2007-01-23
you will be able to play freecell.
:lolflag:

---

### Post by tribaal on 2007-01-23
Unfortunately , VMware is not an answer yet. But they are working on a direct rendering version. I wouldn't hold my breath however.

In the mean time, I use wine. It's more than enough for *my* gaming needs, but your best options for games still is to boot a "Wintendo" partition (i.e., windows used only for gaming) ;)

- trib'

---

### Post by Moodel on 2007-01-23
Thanks for the relies all. I've had the same answer from elsewhere and thought there would be an issue with the 3D graphics.

Ah well...guess I'll play the waiting game then :D

---

### Post by leech on 2007-01-23
Last I checked, there was some very preliminary DirectX support, but I never tested out how well it worked.  It would be very cool if we could one day run Windows games with VMWare, though probably Wine will be advanced enough for most things by then.  

A lot of it depends on if VMWare could some how take over all control of the GPU, so that the virtual computer thinks that it has a high-end graphics card.  There really wouldn't be a way to emulate it, and quite frankly having a Windows XP in a virtual setting controlling the output of the video would seem very unstable to me, especially since some video drivers themselves aren't very stable.

Leech

---

### Post by jdong on 2007-01-23
As of now vmware's 3D acceleration of the guest is pretty nonexistent (ok fine, it's completely nonexistent and just promises from vmware that they're gonna do it in the future).

The experimental directX you saw was a way to accelerate the host's rendering of the guest display via DirectX, which is totally unrelated  :)

---

### Post by Entity` on 2007-01-23
I know that you can use wine to run stand-alone games, but my question is how do you run MMOs and the like.  If you wanted to use the multiplayer on a stand alone game on... say Starcraft, wouldnt that cause problems.  Im all for wine and stuff like that but i still need info.

---

### Post by Josh1 on 2007-01-23
> **Entity` said:**
> I know that you can use wine to run stand-alone games, but my question is how do you run MMOs and the like.  If you wanted to use the multiplayer on a stand alone game on... say Starcraft, wouldnt that cause problems.  Im all for wine and stuff like that but i still need info.

I played Diablo 2, Starcraft, Warcraft 3 (Frozen Throne) and CS 1.5 & 1.6 over LAN perfectly on Ubuntu earlier last year. :D

---

### Post by jdong on 2007-01-23
Starcraft BattleNet I know doesn't work in Wine... that causes wine to stack dump. But as noted UDP LAN play does indeed work.

---

### Post by Entity` on 2007-01-23
I should have specified so that my point leaned more towards internet play, but what you provided is still usefull indeed.  But still is wine getting any better?  Does it have a shiny* future?  Can it get you drunk? (cough/snicker) I would love to know as would a lot of people.


*meaning well defined; very good

---

### Post by McQuaid on 2007-02-10
I saw this recently mentioned on osnews about dx8.1 support in vmware for os X, and I assume linux as well.

[http://www.youtube.com/watch?v=xF_CoXsXtk4](http://www.youtube.com/watch?v=xF_CoXsXtk4)

Looks promising.  I was curious about non 3d accelerated games.  I have some classics like abe's exxodus that do not work in wine.  What's the performance like of 2d games, that have pre rendered cinematics and such?

Also, I've never ventured into using vmware.  If my older games run fine in win98, wouldn't that be a better choice to cut down the resource demands instead of xp?

---

### Post by fang64 on 2007-02-15
you do have light support of 3d rendering on vmware workstation 6 ( the beta ) it seems kind of shaky though along the lines of being stable, but it works. Some games however experimenting with it will cause the whole vmware emulation stack to just die and cause a complete lock up. Other times it'll run stable, fusion hopefully will end up on the other platforms but it does indeed work and the beta is out. Unfortunately nothing for the Linux gamer yet I am hoping this changes might give way for some more users to switch from windows I still dual boot for gaming purposes since Cedega can't emulate everything quite yet.

---

### Post by Breepee on 2007-02-15
I've seen the YouTube video too and it looks very promising. I hope it can solve all my gaming woe's sometime in the near future, but it will need to support DX9 too. We'll see.

---

