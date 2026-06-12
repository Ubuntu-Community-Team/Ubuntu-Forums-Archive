---
title: "Playing Alpha Centauri/Alien Crossfire--And General &quot;Getting Wine to Work&quot;"
date: 2006-08-04
forum: Gaming &amp; Leisure
---

### Post by Steggy on 2006-08-04
Hiya all,

Right now, I use Windows for one thing and one thing only--games. While quite a few of the games I play are emulation (and therefore easily playable on Ubuntu), some are Windows-only. I pretty much can't do with out those few, and so I'm stuck dual-booting instead of just running Ubuntu like I want to (I don't have the RAM to to virtualize at the moment.)

And so I've come here, hoping someone can help me out.

At the moment, what I really want to get working is Sid Meier's Alpha Centauri/Sid Meier's Alien Crossfire--a pretty old game, but one of the best I've ever played. In Windows I have it installed on the drive I share between Windows and Ubuntu (which is formatted to ext3.) When I try to run the game, the screen changes to black for a few moments, then crashes back to my desktop, so I tried to run it from the terminal, and I got this output:

```
josh@midgar:~$ wine /sharedDrive/windows/programs/alphaCentauri/axstart.exe
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd49148)->(0x10022,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 8
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 8
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd49148)->((nil),00000008)

```

Has anyone gotten SMACX to work in Ubuntu using wine, or does anyone know how I can fix whatever is causing this problem?

I'd like to try to figure this out myself, but I have no idea whatsoever as to what's going on, which brings me to my next question: where I can go to learn about configuring/fixing wine to get it to run whichever programs I want it to? I'm sure I'll be running into problems with pretty much every game or other program I try to run, and instead of having to ask for help at the first sign of trouble, I'd like to be able to work on the problem myself. The thing is, I don't even know where to begin looking to troubleshoot wine myself.

Thank you in advance for any and all help,
Steggy

---

### Post by Harleen on 2006-08-04
Wine - the eternal mystery... I wish it would run just at least one  of the programs I want.
So no, I cannot help you very much with the wine configuration. But the error message is saying, that your X-Server is not configured for 8 bit colour depth, but the game tries to change to that resolution. If you add the 8 bit colour depth to your xorg.conf, the game should crash at another point.

If you're really desperate, you could try out the Linux version of SMACX. But I assume, you don't want to invest 30 Euro on a game, that you already own.

---

