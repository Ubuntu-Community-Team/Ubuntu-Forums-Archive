---
title: "anything better than DesmuMe?"
date: 2009-11-15
forum: Gaming &amp; Leisure
---

### Post by JamesParnell on 2009-11-15
i downloaded it yesterday, and downloaded a test game to try it on (just happened to be harvest moon, lol) and when it started i had a 45fps, but after i hit the main menu (the "touch screen start thingy" it dropped to 4-5fps, and i had to close as it was not playable, is that just the price for DS emulators?? or is there a better one to use?

---

### Post by hikaricore on 2009-11-15
What kinda hardware you got?  I've had mixed luck on a 3ghz dualcore system.

---

### Post by CharmyBee on 2009-11-15
Try using the software renderer. 

I have no idea why the emulator authors thought using OpenGL for something better accomplished via means of Software (especially without filtering) is a good idea, there are no benefits from it.

---

### Post by hikaricore on 2009-11-15
> **CharmyBee said:**
> I have no idea why the emulator authors thought using OpenGL for something better accomplished via means of Software (especially without filtering) is a good idea, there are no benefits from it.


Uhh.... no benefits from using hardware rendering instead of software rendering?
You're completely insane.

---

### Post by CharmyBee on 2009-11-15
> **hikaricore said:**
> Uhh.... no benefits from using hardware rendering instead of software rendering?
You're completely insane.

- The textures are low color, and resolution and never have texture filtering. 
- Polygon counts are always under 2048 triangles per screen, amounts of vertices that aren't too daunting for even a Pentium Pro 200 to process entirely in software.
- Very basic blend modes. 
- Screen resolution is strictly low by design. OpenGL use would be even more useless here.
The 3D technology in the Nintendo DS is strictly by '97 3d standards, its unrealistic to demand a high requirement for OpenGL, a 3D card and a 2Ghz+ processor to do what graphics the NDS can do. The only big thing about it is to render two of these small resolution screens at once while sampling stylus touch at 60hz.

 Had someone experienced with emulation programming from the '90s write a NDS emulator in Assembly and C, with a software renderer at its core, it would probably be running full speed on a Pentium III 1GHz. NO$GBA is the closest (and most accurate) to this i've seen, but it is closed source and is donationware.

---

### Post by Azatos on 2009-11-15
> **JamesParnell said:**
> i downloaded it yesterday, and downloaded a test game to try it on (just happened to be harvest moon, lol) and when it started i had a 45fps, but after i hit the main menu (the "touch screen start thingy" it dropped to 4-5fps, and i had to close as it was not playable, is that just the price for DS emulators?? or is there a better one to use?

I run it at the same speed on ubuntu as windows.  Also fairly decent speed from the latest svn 40fps or better.  The latest official release of desmume isn't good if you know how to compile and whatnot I'd suggest you do that.  Also that game just got released so it might not be able to emulate it properly.

---

### Post by JamesParnell on 2009-11-16
well, im using a NC10 netbook. which will probably be the reason. 1.6ghz atom...netbooks -_-.

---

### Post by Tumdian on 2009-11-16
I know it's not a native application, but No$GBA runs beautifully for me in Wine.

---

### Post by hikaricore on 2009-11-16
> **JamesParnell said:**
> well, im using a NC10 netbook. which will probably be the reason. 1.6ghz atom...netbooks -_-.

There's your problem.  Desmume is serious cpu intensive.

---

### Post by scared0o0rabbit on 2009-11-16
> **Tumdian said:**
> I know it's not a native application, but No$GBA runs beautifully for me in Wine.

Speaking of no$gb through wine, does it work with gamepads?  In particular, with an xbox controller plugged into the USB?  I can't get visual boy advance to pick up input from it, so I'm trying to find a different program to try instead for GBA emulation.

---

### Post by Tumdian on 2009-11-17
I use a cheap game pad that I bought from walmart a couple of years ago, and it works pretty well within no$gba in Wine.  I'll post the model, if you'd be interested.  I think I picked it up for 15 bucks, or something.  I'm sure it's slightly cheaper now.

---

