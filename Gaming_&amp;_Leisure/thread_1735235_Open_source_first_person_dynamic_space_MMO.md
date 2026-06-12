---
title: "Open source first person dynamic space MMO"
date: 2011-04-21
forum: Gaming &amp; Leisure
---

### Post by stealth. on 2011-04-21
So I've been looking into this for a while and although I don't have time *right now*, I will have some time later. I want to make a open source "space" MMO. 

I don't mean this to be dictation, but it WILL NOT be skill based. I don't like it when people to have to play for hours and hours just to be able to do something. I personally think it should be money based, but that is up to everybody that contributes. Money based means that you have a chance to find a large mine with valuable minerals, or run across the rings of a planet and find some minerals there and sell them for a nice profit to buy a new weapon or ship. 

Now the difference between this and EVE is that you will be able to visit planets seamlessly. You can start at your "home" take off, go into space, fight the invaders you saw from the ground, come back and land, without a loading screen. Another difference from EVE is that this will be first person. 

I've been pondering this for a long time, but recently I've found something similar:  (proprietary) [http://en.wikipedia.org/wiki/Infinity_%28MMOG%29]("http://en.wikipedia.org/wiki/Infinity_%28MMOG%29")



I think we should use the Ogre3d Graphics engine: [http://www.ogre3d.org](http://www.ogre3d.org) 
Its very nice, can support procedural planets, uses C++, and runs perfectly on Linux.

If anyone wants to help, please leave a reply. If this did work out, it would probally be the greatest game ever, and it would run natively on Linux. 

(I can't wait to come to land on a planet, get my ship lasered in half, eject, parachute safely in my little pod, and fight for my life)

---

### Post by user1397 on 2011-04-21
> **stealth. said:**
> So I've been looking into this for a while and although I don't have time *right now*, I will have some time later. I want to make a open source "space" MMO. 

I don't mean this to be dictation, but it WILL NOT be skill based. I don't like it when people to have to play for hours and hours just to be able to do something. I personally think it should be money based, but that is up to everybody that contributes. Money based means that you have a chance to find a large mine with valuable minerals, or run across the rings of a planet and find some minerals there and sell them for a nice profit to buy a new weapon or ship. 

Now the difference between this and EVE is that you will be able to visit planets seamlessly. You can start at your "home" take off, go into space, fight the invaders you saw from the ground, come back and land, without a loading screen. Another difference from EVE is that this will be first person. 

I've been pondering this for a long time, but recently I've found something similar:  (proprietary) [http://en.wikipedia.org/wiki/Infinity_%28MMOG%29]("http://en.wikipedia.org/wiki/Infinity_%28MMOG%29")



I think we should use the Ogre3d Graphics engine: [http://www.ogre3d.org](http://www.ogre3d.org) 
Its very nice, can support procedural planets, uses C++, and runs perfectly on Linux.

If anyone wants to help, please leave a reply. If this did work out, it would probally be the greatest game ever, and it would run natively on Linux. 

(I can't wait to come to land on a planet, get my ship lasered in half, eject, parachute safely in my little pod, and fight for my life)
i'm pretty sure i've heard of an open source mmo native linux game recently that is also space themed, might be something to look into (i'm not sure if it is exactly like your concept, but if it is very similar it would probably make more sense to join their development team than to try and start your own project).  i'm gonna search for it right now and if i find it i'll post the link here

edit: wow...haha nevermind, i was thinking of the closed-source, and subscription-based [vendetta online]("http://www.vendetta-online.com/") (although it is native for linux) :lolflag:

---

### Post by stealth. on 2011-04-21
> **ubuntuman001 said:**
> i'm pretty sure i've heard of an open source mmo native linux game recently that is also space themed, might be something to look into (i'm not sure if it is exactly like your concept, but if it is very similar it would probably make more sense to join their development team than to try and start your own project).  i'm gonna search for it right now and if i find it i'll post the link here


Alright thanks :)

---

### Post by zipperback on 2011-04-25
What license do you intend to release the game under?

- zipperback
- :popcorn:

---

### Post by stealth. on 2011-04-25
> **zipperback said:**
> what license do you intend to release the game under?

- zipperback
- :popcorn:

gnu gpl?

---

### Post by zipperback on 2011-04-25
The reason I was asking is because the recent version of OGRE is under the MIT license now and not the LGPL as previously released.

- zipperback
:popcorn:

---

### Post by KIAaze on 2011-04-26
I don't think dynamically linking a GPL program to an MIT-licensed library like Ogre is a problem. (In fact, in this case, it should even be possible to statically link.)

I'm not too optimistic, but I hope you'll get it done. :)

Here are some related interesting MMO projects:
[http://www.projectbossanova.com/about](http://www.projectbossanova.com/about)
[http://www.planeshift.it/](http://www.planeshift.it/)
[http://dev.ryzom.com/](http://dev.ryzom.com/)
[http://www.forsakensanctum.com/index.php](http://www.forsakensanctum.com/index.php)

I think another MMO was started here on the forums, but I can't remember it now.

Personally, I'm staying away from MMOs (so I am a bit disappointed about bossanova's final choice :/ ).

---

### Post by stealth. on 2011-04-28
It will happen, eventually. Its going to take the help of other people though. Currently I'm working on [https://github.com/cgroza/wx-Youtube](https://github.com/cgroza/wx-Youtube). I started working on this to improve my C++ skills for the game that I will make.

---

