---
title: "Valve is the #1 reason I will not get rid of windows."
date: 2007-05-02
forum: Gaming &amp; Leisure
---

### Post by lebe0024 on 2007-05-02
If I could play Source related games (CS, upcoming Team Fortress 2) natively on linux, with reasonable framerates and graphics, I would switch to linux in a heartbeat. OH HOW I WISH VALVE WOULD PORT THEIR SOFTWARE TO LINUX! :( 

Tell me, for those of you who run Source games with WINE:
1) Is it software rendered?  Or does WINE use opengl to implement the DirectX API?
2) How much of a performance penalty do you have compared to windows on the same hardware?
3) What features, graphical or otherwise, do not work under WINE?  I already know about the microphone issue, but do you only get directX 7/8 graphics?

---

### Post by lordhebe on 2007-05-02
> **lebe0024 said:**
> If I could play Source related games (CS, upcoming Team Fortress 2) natively on linux, with reasonable framerates and graphics, I would switch to linux in a heartbeat. OH HOW I WISH VALVE WOULD PORT THEIR SOFTWARE TO LINUX! :( 

Tell me, for those of you who run Source games with WINE:
1) Is it software rendered?  Or does WINE use opengl to implement the DirectX API?
2) How much of a performance penalty do you have compared to windows on the same hardware?
3) What features, graphical or otherwise, do not work under WINE?  I already know about the microphone issue, but do you only get directX 7/8 graphics?

1) No it uses proper hardware accelerated graphics.
2) Very little, about 5 FPS in the worst cases.
3) HDR. That's about it.

---

### Post by wizardofyendor on 2007-05-02
I don't know about source games, but I've ran WoW in wine on occasion, and I can tell you a few things about wine.

It does use convert Direct3D to OpenGL, believe it or not the performance hit is minimal (as long as your running it full screen, running it windowed has funny effects).

---

### Post by ghandi69_ on 2007-05-02
I spent about an hour trying to get CS:Source to work... and the game worked seemingly flawlessly except for one thing.... Every flash grenade that blew up in my view would cause the to lock up for 5 sec.. 

That was all the farther I got.

---

### Post by aidanr on 2007-05-02
i'd love it too but valve doesn't seem interested (could be something to do with the fact that two of valves main guys are ex microsoft employees) there's already a huge thread on the steampowered forums requesting a linux client but as far as i can see valve has ignored it

i'd image porting the source engine would be a lot of work but half-life 1 based games use opengl and are based off the quake engine so it wouldn't be much work to port them at least

maybe in the future they will as linux and mac gain more popularity, but in the meantime vote with your wallet and support game devs who do cross platform games like id and epic

---

### Post by a12ctic on 2007-05-02
Its sort of a joke that they have a server client (That pretty much all the servers use, at least 60% of them probobly), yet they dont provide a user client. It's like they know they need linux for stable servers, but they dont want to give us the client, that wouldnt even take a lot of work to get running. Its a joke. Completely unfair.

---

### Post by justin whitaker on 2007-05-02
CS:S and HL2 runs great on Crossover Office, and on Cedega. Minimal FPS hit, if any, and better latency when connected to servers. 

Steam titles are not a good reason to stay on XP. :)

---

### Post by SBFC on 2007-05-02
> 1) Is it software rendered? Or does WINE use opengl to implement the DirectX API?

You can actually tell all those Steam games to run in opengl mode by setting the '-gl' flag in the launch options. 

As for me, HL2 and CS:S run perfectly well in Wine.

---

### Post by ArtificialSynapse on 2007-05-02
EDIT: Changed my mind.

---

### Post by FoolsGold on 2007-05-03
> **SBFC said:**
> You can actually tell all those Steam games to run in opengl mode by setting the '-gl' flag in the launch options. 
Does that actually work though? I've tested the -gl flag in Windows out of curiosity and didn't see any evidence it did anything. Graphically it didn't do anything, the advanced video options still reported DirectX in use. Heck, I can't even find any Valve documentation which state the -gl flag even **EXISTS**. It seems more like a rumor that someone spread and people latched onto it without bothering to double-check the facts.

As for me, Valve games were also my primary reason for staying with Windows, but it occurred to me that this meant that Valve had a very strong leash on my ability to choose how to use my computer. I didn't like that - if Valve really wants to ignore the massive thread on their official forums stating strong support for a Linux port of Steam and their games, then I have no choice but to vote with my feet.

I'm considering attempting to run some of their games in Wine, but if they don't work well enough, meh, I won't care. If it's really important, stick with Windows. Eventually games will become less important and you'll be able to switch, probably.

---

### Post by RandySavage on 2007-05-03
> **aidanr said:**
> i'd love it too but valve doesn't seem interested (could be something to do with the fact that two of valves main guys are ex microsoft employees) there's already a huge thread on the steampowered forums requesting a linux client but as far as i can see valve has ignored it

i'd image porting the source engine would be a lot of work but half-life 1 based games use opengl and are based off the quake engine so it wouldn't be much work to port them at least

maybe in the future they will as linux and mac gain more popularity, but in the meantime vote with your wallet and support game devs who do cross platform games like id and epic

You're probably right about the favoratism manifesting itself because of x-Microsoft employee influence.

That and the absolute dominance Windows has on desktops.

---

### Post by SBFC on 2007-05-03
> Does that actually work though? I've tested the -gl flag in Windows out of curiosity and didn't see any evidence it did anything. Graphically it didn't do anything, the advanced video options still reported DirectX in use. Heck, I can't even find any Valve documentation which state the -gl flag even EXISTS. It seems more like a rumor that someone spread and people latched onto it without bothering to double-check the facts.


Before I used the -gl option any water in HL2 would show up as plain ole white. It'd be just a large white texture, no matter where I was. After using the -gl flag the water rendered perfectly. Nice and blue, and I was able to see through it.

If you plan on giving them a go with Wine, use the '-novid' flag as well, as the opening Valve vid takes __forever__ to run through.

---

### Post by bastiegast on 2007-05-03
> **SBFC said:**
> Before I used the -gl option any water in HL2 would show up as plain ole white. It'd be just a large white texture, no matter where I was. After using the -gl flag the water rendered perfectly. Nice and blue, and I was able to see through it.

If you plan on giving them a go with Wine, use the '-novid' flag as well, as the opening Valve vid takes __forever__ to run through.

Like lordhebe said, everything works perfectly except HDR. If you enable GLSL in the wine registry you can play the games with all the fancy effects you can imagine with little or no performance loss.

About the intro vid, It's slow sometimes for me too, but after the latest wine update it was normal again. I remember it has been normal before but not for long time so you better disable it.

Edit: My English is getting crappy and vague I should probably go to sleep :p

---

