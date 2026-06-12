---
title: "Is it possible to install DirectX 9.0c?"
date: 2007-06-07
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2007-06-07
Today I've tried to install DirectX 9.0c with [Wine-Doors](http://www.wine-doors.org/wordpress/), but the Wine-Doors download/installation progress bar for DirectX freezes always at 0%.

I thought it's not necessary/possible to install DirectX.

Can I install [DirectX 9.0c](http://www.softwarepatch.com/windows/directx.html) with Wine instead? I would love to see some water effects and HDR in CSS.

THX!

---

### Post by loathsome on 2007-06-07
> **ubu-for said:**
> Today I've tried to install DirectX 9.0c with [Wine-Doors](http://www.wine-doors.org/wordpress/), but the Wine-Doors download/installation progress bar for DirectX freezes always at 0%.

I thought it's not necessary/possible to install DirectX.

Can I install [DirectX 9.0c](http://www.softwarepatch.com/windows/directx.html) with Wine instead? I would love to see some water effects and HDR in CSS.

THX!
No, but I think Cedega already use it - give that a try instead, Wine isn't for games.

---

### Post by aoanla on 2007-06-07
> **loathsome said:**
> No, but I think Cedega already use it - give that a try instead, Wine isn't for games.

Erm.

If Wine isn't for games, then why do all the updates for wine have more changes to Direct3D than to any other subsystems?
Similarly, if Wine isn't for games, then why is the Wine AppDB full of Games, especially at the Platinum and Gold levels of functionality?

It certainly *looks* like Wine is for games.

---

### Post by ubu-for on 2007-06-07
> **loathsome said:**
> No, but I think Cedega already use it - give that a try instead, Wine isn't for games.

Counter-Strike Source (CSS) and World of Warcraft (WOW) work great with Wine!

I've tried to install DirectX with Wine without success, but I wonder how can Wine-Doors offer the installation of DirectX 9.0c?

---

### Post by hikaricore on 2007-06-07
> **loathsome said:**
> No, but I think Cedega already use it - give that a try instead, Wine isn't for games.

Cedega for one does not use directx, it uses hacks based on wine/winex to force games to work.  Second wine is definately for games as well as applications.

--

While it is possible to install directx (somewhat) under wine, it is not in any way useful.

Wine can not use the files directx provides and will not be able to do so pretty much ever.

---

### Post by loathsome on 2007-06-07
Well, I might've said that wrong.

What I meant was that Cedega is much better with games than Wine. I do play Half-Life 2 and Episode One in Wine without any problems at all, but they run much smoother in Cedega.

I basically use Wine for windows-only apps, and Cedega for some games.

---

### Post by AndrewRiedi on 2007-06-07
> **loathsome said:**
> Well, I might've said that wrong.

What I meant was that Cedega is much better with games than Wine. I do play Half-Life 2 and Episode One in Wine without any problems at all, but they run much smoother in Cedega.

I basically use Wine for windows-only apps, and Cedega for some games.

Also WRONG.  Wine has more advanced D3D support than Cedega.  Wine is faster than Cedega.  Wine is beginning to support some more advanced copy protection.  Wine is developing faster than Cedega.  The only things that Cedega has in support for games that Wine doesn't is that they allow themselves to use petty, worthless hacks to make a couple games kinda, sorta, work.  Then they build hacks on top of hacks on top of hacks.  It really should be obvious by now what happens when you take that kind of development solution.  Your initial development is quite fast, but it slows down just as fast.  This is what we are seeing with Cedega, while Wine development is as fast as ever.  Because of these hacks, Cedega is able to support a few games that Wine cannot yet support, but the reverse is also true.

---

### Post by tht00 on 2007-06-07
I'm really not sure what installing DX through Wine would do, as Wine already has (many) DX functions implemented.

If I recall correctly, DX interfaces to the video card through the Windows driver and provides an API to program to.  In Linux, there is no such driver to interface to, but rather, the DX calls are converted to OpenGL calls.  Really, I'm pretty sure every Windows API call is converted to a Linux-comparable one.

---

### Post by hikaricore on 2007-06-07
> **tht00 said:**
> I'm really not sure what installing DX through Wine would do, as Wine already has (many) DX functions implemented.

Again, nothing at all is what it would do.  ^_^

---

### Post by jimminy_kriket on 2007-06-07
> **AndrewRiedi said:**
> Also WRONG.  Wine has more advanced D3D support than Cedega.  Wine is faster than Cedega.  Wine is beginning to support some more advanced copy protection.  Wine is developing faster than Cedega.  The only things that Cedega has in support for games that Wine doesn't is that they allow themselves to use petty, worthless hacks to make a couple games kinda, sorta, work.  Then they build hacks on top of hacks on top of hacks.  It really should be obvious by now what happens when you take that kind of development solution.  Your initial development is quite fast, but it slows down just as fast.  This is what we are seeing with Cedega, while Wine development is as fast as ever.  Because of these hacks, Cedega is able to support a few games that Wine cannot yet support, but the reverse is also true.

I dont know how you can tell him he's wrong if cedega is indeed faster than wine on his personal computer.

---

### Post by AndrewRiedi on 2007-06-08
> **jimminy_kriket said:**
> I dont know how you can tell him he's wrong if cedega is indeed faster than wine on his personal computer.

There are a few cases in which Cedega is faster.  However, for the mass majority of cases, Wine is faster.  So although he is obviously correct for his personal case, he is not correct for the general case.

---

### Post by Clopy on 2007-06-15
> Can I install DirectX 9.0c with Wine instead?

I had the same problem with wine-doors and directX. I couldn;t also install directx9 that came with some of my games. Finally I took a look at what wine-doors is doing and managed to install directx. Just download the redistributable from here:

[ftp://203.123.69.202/games/microsoft/directx_9c_redist.exe](ftp://203.123.69.202/games/microsoft/directx_9c_redist.exe)

Then just wine directx_9c_redist.exe where you downloaded it and it will install just fine.

---

### Post by weblordpepe on 2007-06-15
To my understanding, that would break wine.
Wine uses fake versions of those DLL files to wrap into openGL and stuff. I know that there are some DLLs that if you replace with normal windows ones, then it breaks wine.

---

### Post by Magnes on 2007-06-15
But WINE has it's DLL-s protected I suppose? You could choose what version to use with what application (wine version or native version), so installing DirectX should do nothing to WINE.
Also you could (or even MUST for newer games) install some additional DirectX DLL-s that work with WINE and provide some updates for DirectX. They are not implemented by WINE but they work fine (the are named like this: d3dx9_33.dll).

---

### Post by hikaricore on 2007-06-15
Again unless you know what you're doing and an application specifically won't install because directx hasn't been "installed", you should NOT be installing it.
It will not benfit you in any way and will do nothing 99% of the time  other than possibly causing stability issues in wine.

WINE does not use the files installed by the directx installer unless forced to, and forcing wine to use any of these libraries will more than likely just cause it to crash.

---

### Post by shadows85 on 2007-06-24
> **loathsome said:**
> No, but I think Cedega already use it - give that a try instead, Wine isn't for games.

Meh cedega is a scam..

---

### Post by hikaricore on 2007-06-24
I don't see the point of bashing Cedega in a thread that has been dead for a week.
The original question of this thread has been answered, and I will not have it turn into another wine vs. cedega debate.

Thread closed.

---

