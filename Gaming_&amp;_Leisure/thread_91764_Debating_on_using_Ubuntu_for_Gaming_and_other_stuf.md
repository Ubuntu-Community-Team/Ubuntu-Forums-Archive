---
title: "Debating on using Ubuntu for Gaming and other stuff..."
date: 2005-11-18
forum: Gaming &amp; Leisure
---

### Post by Goddess_of_Linux on 2005-11-18
I have another thread started in Community Chat and someone said that Ubuntu wouldn't play my DirectX games and that has me a little concerned.
Does Linux have the ability to play those games? And if not or if so, then how is the graphics of those games?

---

### Post by ltmon on 2005-11-18
Hi,

Out of the box no Linux system will not play any windows games.  It's just simply a different system.  

But some bright folks have written a compatability layer, called "Wine".  Wine can run many (non directx) windows applications quite well.  Later another group of people created "winex" which was wine with directx.  Later it was renamed "Cedega". 

It is a commercial product, sold by Transgaming.  You can go look at it (google for cedega) on their website and they have a list of games that they support.

It will cost money for cedega, and it only supports a limited list of games, but it will stop you having to reboot the computer into windows every time you want to play a game.

L.

---

### Post by rpgcyco on 2005-11-18
You can get the above mentioned Cedega [here](http://www.transgaming.com/). Don't expect much however. Compatibility is pretty poor and it breaks often [especially with Steam + Steam Games].

Also, performance of your games will reduce significantly, unless they have OpenGL renders. For instance, Counter-Strike: Source in Windows run at about 60-100FPS on my machine, but with Cedega, it barely manages 35. Which IMO, is totally unplayable. Reducing the res and detail does little to help, and my Cedega config is spot on.

There are quite a few native clients for games though. UT, UT2003, UT2004, Doom3, Quake 1 to 4, Neverwinter Nights, Return to Castle Wolfenstein, Enemy Territory, Americas Army. Not to mention Warcraft III and WoW work well in Cedega [and even WINE], when run with the --opengl flag. There are some good GNU games, such as Nexuiz.

- Rpg Cyco

---

### Post by YokoZar on 2005-11-18
[QUOTE=ltmon]Hi,

Out of the box no Linux system will not play any windows games.  It's just simply a different system.  

But some bright folks have written a compatability layer, called "Wine".  Wine can run many (non directx) windows applications quite well.  Later another group of people created "winex" which was wine with directx.  Later it was renamed "Cedega". [/quote]This is misinformed.  Wine has better DirectX support than Cedega.

For instance, Wine can run Half Life 2 in DirectX 9 mode natively, wheras Cedega has to run it in DirectX 7 mode.

As for performance, we've gotten mixed reports, but the free Wine has outperformed Cedega in many cases and in some it even outperforms Windows.  This is in part due to Linux's superior memory management, in part due to a lack of bloat, and in part due to significant differences in Wine, Cedega, and Window's implementation of the same API.

I highly suggest going the Wine route.  Try the packages from winehq, and see this thread: [http://ubuntuforums.org/showthread.php?t=91369](http://ubuntuforums.org/showthread.php?t=91369)

---

### Post by rpgcyco on 2005-11-18
> For instance, Wine can run Half Life 2 in DirectX 9 mode natively, wheras Cedega has to run it in DirectX 7 mode.

Cedega runs CSS in DirectX 8 mode by default, on my machine. I'm assuming it can run HL2 in DX8 as well.

Wine is definately going in a better direction than Cedega, IMO, but I have never got it to run HL2 or CSS before.

- Rpg Cyco

---

### Post by ramba on 2005-11-18
If you like quake, and loved the trickjumps of AQ2, you should try [warsow]("http://www.warsow.net/").

There's no doubt that Windows has the upper hand when it comes to games but linux has its fare share of good games too. :cool:

---

### Post by Goddess_of_Linux on 2005-11-18
Thanks for all the reply's, especially rpgcyco and YokoZar... I am thinking about installing Ubuntu, but under the live copy I am having a problem with it letting me set my display to 1280x1024 @ 85 Hz. Can anyone help with that...

---

### Post by cluelessnoob on 2005-11-18
I think it plays direct X..... I can run Wow and Frozenthrone on them.

I haven't tryed Cadega but I think you have to pay for a subscription.

I've read that they don't really offer much more support than wine. 

the key is the -opengl command and it actually looks better then my windows installs.  

I dont know if other developers games work though... I'm kinda of a noob system admin wise in linux.  I"m about to go get Age of Empires III and Black and white 2 and try them out.  So far I'm impressed with the performance but annoyed with the set up time.  Ubuntu has my vote though... I love this distro.  A great community and is the closest thing I"ve seen to bridge the gap to a good desktop linux.

I've never tryed the live install for ubuntu, doesn't that custom compile your kernel?  I think its overrated and takes a long time when I tried it with gentoo.

---

