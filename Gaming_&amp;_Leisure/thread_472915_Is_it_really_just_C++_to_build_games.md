---
title: "Is it really just C++ to build games?"
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by tocleora on 2007-06-13
I posted a comment on this thread today on digg:

[http://digg.com/apple/Did_Apple_Lie_to_Mac_Gamers](http://digg.com/apple/Did_Apple_Lie_to_Mac_Gamers)

In reference to the fact EA Games will now be supported on Mac which to find out was Transgaming's Cider that was actually being used.  I mentioned I thought it was still in the right direction and that if transgaming got support for mac from EA then they'd have the knowledge to also make cedega (or cider) work better for linux as well.  Someone responded with this:

> Just out of curiosity I wonder how much more difficult it would be to just make a native port over working with Cedega to iron out all the bugs. Will the time spent working out Cedega issues be more or less than the time required to just make a native port of a game?

This stuff is still written in C++ and C++ is C++. cout works just the same on linux as it does on a PC or a mac.

For crying out loud why can't developers just use OpenGL/SDL over DirectX and then we wouldn't even need these conversations.

Anyone who thinks that Direct3D is superior to OpenGL is believing a lie plain and simple.

They wouldn't even need an emulator if they just made it cross platform to begin with. . . it's really not that hard.

Is it *really* that easy?  I would think that several factors would need to be considered not only for porting to linux but the various distros.  No?

---

### Post by cogadh on 2007-06-13
Yes it is really that easy, but not all games are actually written strictly in C++. It is very likely that the graphics and physics engines are written in C++, but much of the game could be written in a completely different language that has C extensions (like Python).

The problem is 95% of PCs run Windows with DirectX, so it makes sense for developers to program for DirectX and not OpenGL/SDL. DirectX works and it is relatively easy to program for, especially when most game designers are using third party engines instead of building them in-house. The 5% of PC users who have alternative OSes are not a large enough customer base to warrant the expense of developing a game to be cross-platform, when much less expensive DirectX-based solutions are out there.

---

### Post by fatsheep on 2007-06-13
I'm no game developer but you are correct that C++ is C++ (for the most part).  There are different strains and standards but just about everything is the same (or should be).  The biggest issue, I think, is what you pointed out - DirectX.  DirectX is Microsoft's Windows only 3d platform.  If everyone switched to OPENGL then porting would be simple.  Look at Unreal Tournament and Quake.

---

### Post by Limpan on 2007-06-13
Then OpenGL is a proper standard which DirectX isn't. At least not the last time I checked. But this is not really something most people care about and since you can make good money with DirectX there's really no use to code for/with OpenGL. It's sad.

---

