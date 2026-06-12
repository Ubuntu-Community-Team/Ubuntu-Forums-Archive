---
title: "Terrible graphic glitchiness-- is my GPU fried?"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by MaxIBoy on 2008-09-21
Long post, I know, but bear with me. 



I have a Radeon HD 4850 with fglrx drivers. I've got it set at 1280*1024, 60 hz.


Other games have exhibited other, less debilitating glitches, but the worst so far was just now, early on in an ETQW game. This was the first ETQW game I'd played since I got rid of Windows a while back, and I just got the Linux version of the game installed today. (I used these instructions: [http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/)) The latest update didn't work (I got segfaults when I said "yes" to the prompt of whether I wanted to exit the game and execute the .run patch, even if I ran the game with root privileges.) I finally decided to update it later and started playing against the computer. Maybe two minutes into the game it started glitching.

It's hard to explain, but basically it was as if 15 or 20 individual polygons from the given scene are being selected at random and expanded until they combine to fill or nearly fill the screen. This process seems to have been repeated at every frame, so it was flashing too fast to tell for sure. If you've ever played ETQW, I was on the "refinery" map, so they were mostly brown with a few white ones and very few gray ones. I was in the area of the map just outside the initial GDF spawnpoint, where the dirt road dips into a shallow part of the water. The glitchinesses were enough to make it almost impossible to navigate and definitely impossible to fight, but I was playing the easy bots so I stayed alive. (I was able to find sweet spots where the glitches would disappear so I could see the enemies, then aim by memory from there.) I did some experimenting and figured out some details about the problems.

I could make it go away by looking straight up, and not moving (although it still comes back for a split second every five seconds or so.) Often these glitches would only cover part of the screen. When that happened, they would combine with a purple blurry trail effect that looked like failed ztrick glitches. I don't have screenshots because I couldn't find the right button in the game, the Ubuntu screenshot utility doesn't work with a game in fullscreen, and I don't want to put my hardware at risk by running the game again. 



Also, just now compiz went crazy. Individual windows wouldn't refresh their displays unless I switched between workspaces and then back. The mouse moved around just fine though. Also, the fusion icon, when clicked, would cause everything on the screen to shift upwards (although the clicks registered as somewhere else entirely, I had to fumble around blind with the mouse until I finally managed to switch to the Xfce window manager, which fixed it.) Seriously, that happened while I was typing this, which was the first time anything like this has happened.

In case you were wondering, I always have it switched to the Xfce window manager when gaming. When the game glitched out I had to hit ctrl-alt-backspace to get rid of it, that's when Compiz turned itself back on.


Other games have similar problems. Alien Arena has a problem where, on ctf-atlantis (see screenshot) the upper surfaces of the raised beams on the sides of the hallways would randomly flash bright colors, mostly green. It would be part normal and part weird, as if the two were z-fighting. See attached picture. This doesn't happen 100% of the time. Also, the phoronix 3d benchmarks ran perfectly but were glitchy in places. Possibly unrelated, fullscreen flash videos sometimes crash my computer.




The way I see it, this could be caused by a few different things:

[LIST]
[*]Fglrx not supporting my hardware properly.
[*]Overheating graphics card. Maybe possible, but I think fglrx always has the fans cranked up to 100%. It sounds pretty loud, anyway. I haven't overclocked my GPU.
[*]Overheating memory or other memory problems. I doubt this, though, because I didn't overclock or otherwise modify my memory, and my RAM sticks (g.skill) have huge beefy heatsinks on them.
[*]Overheating CPU (Quad-core Phenom with stock fan and heatsink.) Possible because I've overclocked it from 2.2 to 2.6 ghz.
[*]An actually damaged GPU. I hope not, becuase it's been too many days for me to return it and it cost me a lot of money.
[*]UPS isn't feeding my PC enough power. My PC draws about 500 or 550 watts. A better UPS is on its way, meanwhile I have to live with this one. People here may remember my complaints about the evil Laser Printer O' Doom which sucks up 800 watts and shuts down my PC (recently causing a corrupt partition,) but I've unplugged the UPS before and it kept running (though this was before I made a few upgrades.)
[/LIST]






Are there any software diagnostics I could run? Does anyone have advice? I'm sorry if this post is incoherent or hard to understand, I wrote it in a hurry and I'm feeling "out of it" right now. Plus I'm worried about my expensive equipment.

---

### Post by handy on 2008-09-22
I'd start by eliminating the simple things:

Put your CPU back to standard clock speed.

Make sure your heat sinks are dust free.  An air compressor is good for this; I don't let the compressed air spin my fans as they can be ruined by over revving.  You can carefully use an air compressor on your computer with the side off, cleaning up the contents without having to remove any internal components. (Usually)

Remove & reinstall the drivers for your GPU.

See where you are at after having done those things.

Also, the ATi Catalyst Control Center will tell you the GPU temperature.

---

### Post by SebNoker on 2008-09-22
Handys got the answer i think to  this

---

### Post by MaxIBoy on 2008-09-22
Okay, I'll look into it when I get home.

---

