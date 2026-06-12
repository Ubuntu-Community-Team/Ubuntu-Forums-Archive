---
title: "Problem: Too fast graphics in games (Ubuntu 6.06)"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by driesel on 2006-07-08
Hi,

A couple of days ago I started configuring my PC with Ubuntu 6.06.
Everything is going really well, accept for the gaming part.
I've tried UT2004 natively and Max Payne using Cedega 5.1.3.
Both boot up nicely and have very good 3D performance.

There's only one major problem:
The graphics (and ONLY the graphics, not the sound) are running way too fast.
Given the exemple of UT2004:

It begins with the intro: The sound is good but the animation of the Nvidia logo is way too fast.
Even the game menus are animated faster than normally would be the case.
But the biggest problem is that also the actual GAMEPLAY is WAY TOO FAST, although -again- sound is good.

Is there any way to fix this odd problem?


greetings,
driesel

---

### Post by driesel on 2006-07-08
Although my GeForce 2 MX400 has some difficulties handling the game,it seems as if the Prey demo runs quite normal under cedega.

Doesn't anybody ever have got the same issue?

---

### Post by _simon_ on 2006-07-09
I've only ever played UT2004 under linux so i don't know about the graphics being "too fast". Maybe you are just getting better performance under Dapper than you are used to?

When you say the game play is too fast do you mean when you play against bots? Without actually seeing what you mean it's hard to understand. Like I said above maybe you are getting better performance now than you used to?

I play Warhammer 40k Dawn of War under cedega and that runs quite a bit quicker than under windows, I can have the graphics and sound set to the highest setting without a problem where as I could not under windows.

---

### Post by driesel on 2006-07-09
Well,

Actually the intro of UT2004 with the nvidia animation is a good example.

In the intro the sound really can't catch up with the graphics.  Like when the logo gets crushed by an alien, the sound has a delay of 1 second or so.

And ingame movement really is too fast, and I've played the Windows version and the difference is big.
It's not that I have better performance because in busy spaces my framerate really drops drastically at 800x600, although movement is still faster.


greetings,
driesel

---

### Post by driesel on 2006-07-10
Phjew,

I managed to solve the problem :) ...

It seems that the problem is AMD64 platform related.
It's got something to do with the internal clock of the CPU.
To make long stories short:
adding a syntax to the kernel boot prompt solves the problem!

While booting your PC, when in grub mode, one should add some text to the normal kernel string.

Googling on HOWTO: Double Clock Speed Problem should give dtailed instructions.

Thanks to tseliot for having found out ;) !

---

### Post by vem0m on 2006-07-10
wish mine ran that fast just so i could set a limti to what i wanted and have fast fluid GFX :P

---

### Post by guillaume228 on 2008-10-04
I know this was posted a while back but I have the same problem. I was wondering if you ever got it fixed. I installed ubuntu as a dual boot. Then when I went back to windows xp to play spore, everything was really fast. Same thing for my steam games like geometry wars, hl2, and hl2 deathmatch. I even tried playing online and I was moving twice as fast as everybody else.
I have an amd athalon 64 processor and nvidia geforce 7900 graphics card.

---

