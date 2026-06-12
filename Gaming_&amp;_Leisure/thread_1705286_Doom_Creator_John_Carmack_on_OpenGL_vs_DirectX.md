---
title: "Doom Creator John Carmack on OpenGL vs DirectX"
date: 2011-03-12
forum: Gaming &amp; Leisure
---

### Post by skipsbro on 2011-03-12
Slashdot links to an article where John Carmack discusses his preference for Microsoft's DirectX over OpenGL. He seems to make sound arguments, but I do not know enough about how both engines work to make a decision on it.

If there are any DirectX or OpenGL programmers out there, what do you guys think about this?

> arcticstoat writes:
"First-person shooter godfather and OpenGL stickler John Carmack has revealed that he now prefers Direct3D to OpenGL, saying that 'inertia' is the main reason why id Software has stuck by the cross-platform 3D graphics API for years. In a recent interview, the co-founder of id Software said, 'I actually think that Direct3D is a rather better API today.' He added, 'Microsoft had the courage to continue making significant incompatible changes to improve the API, while OpenGL has been held back by compatibility concerns. Direct3D handles multi-threading better, and newer versions manage state better.'"

[Link to slashdot article]("http://games.slashdot.org/story/11/03/11/1832205/Doom-Creator-Says-Direct3D-Is-Now-Better-Than-OpenGL")

---

### Post by cobolt01 on 2011-03-12
The problem is that DirectX will never be licensed for an OS besides Windows and no matter how good DirectX is, it's not fair to subject your customers to that kind of torture.

---

### Post by handy on 2011-03-12
> **cobolt01 said:**
> The problem is that DirectX will never be licensed for an OS besides Windows and no matter how good DirectX is, it's not fair to subject your customers to that kind of torture.

Torture!

Compared to trying to get so many Windows games to play properly via Wine. Let alone the plethora that are just plain no goes with Linux.

---

### Post by cossintan on 2011-03-12
Haha, torture...  While it is extremely frustrating that I can't just run my games fluently inside Linux, I've sort of become used to the fact that I just have to have a separate windows partition for gaming.  I hope one day there will be a solution, but we all know it probably wont happen.  As far as the two APIs are concerned, it's my understanding that OpenGL is the primary graphics API used for drawing and rendering 3D animation for movies.  I would say as far as games DirectX is better, but nothing tops open OpenGL when it comes to modeling and creating complex 3D environments for animation.

---

### Post by alexandrius on 2011-03-13
This is so sad :(

---

### Post by Virus666 on 2011-03-14
It is better to read the whole story instead of stuck with quotations...

[http://www.bit-tech.net/news/gaming/2011/03/11/carmack-directx-better-opengl/1](http://www.bit-tech.net/news/gaming/2011/03/11/carmack-directx-better-opengl/1)

> 'It is really just inertia that keeps us on OpenGL at this point,' Carmack told us. He also explained that the developer has no plans to move over to Direct3D, despite its advantages.

'_OpenGL still works fine_,' said Carmack, 'and we wouldn&#8217;t get any huge benefits by making the switch, so I can&#8217;t work up much enthusiasm for cleaning it out of our codebase. If it was just a matter of the game code, we could quite quickly produce a DirectX PC executable, but all of our tool code has to share resources with the game renderer, and _I wouldn&#8217;t care to go over all of that for a dubious win_.'As you see, Carmack has no pesent plan to transfer his projects to **DirectX**. At least **id Tech 5** and **Rage** is going to be **OpenGL**, however it is too early to say same thing for **id Tech 6**...

---

### Post by mastablasta on 2011-03-15
there used to be a time when OpenGL was more capable or at least about the same. but it really seems the development stalled.

---

### Post by Jagoly on 2011-03-15
Man... not a good thing to read after spending 4 hours trying to get oblivion working in wine.

---

### Post by mastablasta on 2011-03-15
Nah Oblivion really deserves to be run in windows and on full graphics. Also don't forget to apply all patches or there might be a nasty surprise waiting...

---

### Post by weasel fierce on 2011-03-15
Direct X doesn't help a lot if you want to release for mac or PS3 either.

---

### Post by mastablasta on 2011-03-16
mac also has low share, but PS3.... hmm

---

### Post by huwjenjinn on 2011-03-17
> **weasel fierce said:**
> Direct X doesn't help a lot if you want to release for mac or PS3 either.

And taking that to it's ultimate conclusion, the mobile market. 

I suspect you can probably extrapolate pretty much any proprietary desktop/laptop driver like Direct3D and OpenGL and if it doesn't fit the mobile market hedge your bets against it.

---

### Post by Simian Man on 2011-03-17
OpenGL and Direct3D are just APIs on top of the same graphics hardware.  Direct3D is updated much more frequently and they are not afraid to remove outdated features.  OpenGL is more of an industry standard in fields other than games, so they need a lot of baggage that's not really useful any more.  Also design by committee is always slower than when a single entity is in control.  That is why Direct3D is a better API.  And it's not even close.

OpenGL, however, can do everything Direct3D can, it just has to rely on extensions to the official API to access them.  Also useful things that are included with Direct3D, especially D3DX, are not part of OpenGL.  Users either have to roll their own or look for 3rd part libraries.

So it's really not so much a question of D3D producing better results, or being more "powerful".  It's just a much nicer tool to work with.

As has been stated, developers who are targeting more than one platform have to implement different graphic backends anyway, and nearly all engines are designed with multiple renderers in mind, so it's not so much of a problem as it used to be.  For independent developers, it's usually best to use an engine like Ogre or Irrlicht that support both OpenGL and Direct3D and are easier to use than either :).

BTW this is very old news!

---

