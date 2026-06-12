---
title: "A Linux Gaming Development Initiative :O"
date: 2008-11-06
forum: Gaming &amp; Leisure
---

### Post by SAHChandler on 2008-11-06
Hi everyone! Long time member, first time poster. Please don't be mean this is just an idea, one I hope could become extremely large.

I'm here today to talk about the current state of gaming in Linux. Let's face it. It's pretty abismal, and it could be a hell of a lot better. One of the main reasons, I think, is that there are many people in the Linux community who would like to make games, but lack the experience to make, or attempt to make, games. 

Which is why I'm here for a proposal. I would like to make a sort of "development kit" which would allow designers or artists to make their own games , as well as a manual to help get them up to speed. 
If you are interested in this at all, please email me at 
[EMAIL="tres@vortexrikers.net"][COLOR="Red"]tres@vortexrikers.net[/COLOR][/EMAIL]

I know it doesn't sound amazing, but I think if enough people gain interest, there could easily be a large indie development scene in Linux.

As of right now this is only in a "pre-production" stage, one might say. And every project always does well if you have enough people helping. You don't even have to have any skills, your input would be enough. 

Thanks for your time. :)

---

### Post by Sayne on 2008-11-06
I took a couple of months to learn the basics of C and C++ for the purpose of making games. I'm currently doing some tests withe SDL. It's cross platform for *nix, mac and windows. Personally, I think this is the best option at the moment. As someone who wants to be a game developer and is just starting out, having the ability to make games for those three major platforms is really important because I can reach a larger audience.

Also, if someone doesn't want to use Linux (for some misguided reason) they can still enjoy my games.

SDL has bindings for many programming languages, so if you don't want to get into something like C/C++, but maybe know some python, install the python-pygame package.

However, if it's a program used to design the graphics, like a Game Development Environment, that I would be interested in. I mean, do you know how much of a pain it is to build things in OpenGL using GL commands? @_@

If it would allow me to code faster and also make game media relatively easier, I'd be interested in something like this.

---

### Post by chkneater on 2008-11-06
Outta curuiosity, what makes it so hard to code games in Linux?  I have some C++ experience so I know it can be tricky, but why should it be harder than "W"?  I would think with the emulators out there, making quality games should be just as time consuming?  I guess since everyone is doing it mostly in spare time and stuff it makes it more difficult. Just curious.Thanx

---

### Post by Sayne on 2008-11-07
That's just the thing. It's NOT more complicated. In fact, if you use the SDL library, you can make the game for W, L, and M all at the same time. You just have to remember to link to one extra library in Windows. That is the only difference. As soon as you link to that, you're code you made work in Linux will work in Windows. It automatically inserts all the windows API stuff you need, and makes OpenGL instances calling DirectX. The rendering is, however done with proper OpenGL.

I don't know why more people don't do it that way, since it will be made for everything.

It's probably the support, (when you think of commercial companies deploying their software) But I dual boot, and when I compile in Windows, my program works just as well as in Linux.

It's written in C, and by virtue can be compiled in C++ because of C++'s compatibility. So you can get going with it right away. Just read the docs, libsdl.org the library is licensed under lgpl, so you can use it with commercial products as well. Be sure to read the license carefully, just so you know.

---

