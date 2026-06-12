---
title: "WoW Performance &amp; Ubuntu"
date: 2005-11-24
forum: Gaming &amp; Leisure
---

### Post by Gordie on 2005-11-24
I'm a fairly new Ubuntu user (1 week now) but I consider myself fairly adept at troubleshooting technical computing issues (hardware / software background), however I can't figure this particular performance issue out.

I got WoW installed through wine on my machine by compiling the source to include the targeting / mouse bugs and that worked great.  I can actually run WoW in a very stable state.  My problem lies in the video performance.

I'm using a 128mb ATI AiW 9600 Pro (i know ATI linux performance isn't on par with nVidia) and in windows I got great performance with this card for wow (avg of 30fps).  

I'm running WoW in OpenGL mode and have noticed an interesting thing, my avg fps is now around 10 - 15, but when I disable the interface with Alt+Z my fps jumps up around 30 - 40 average.

Two questions:

1) Anything I can do to improve this performance?

2) Any WoW players know of any mods that limit the amount of interface items on the screen as I think that's the link between the performance hit.

Any feedback would be greatly appreciated ;)

---

### Post by Gordie on 2005-11-24
./bump

37 views and nobody else has experienced these issues?

---

### Post by disler on 2005-11-25
Hey,

I've been trying to get some decent frame rates out of WoW for around a week or so now without much success. I seemed to be forever stuck around 20-25fps normally, or 5fps outside the IF bank, that is until I came across your post.

I'm experiencing the exact same issue, frame rate outside of densly populated areas is around 20fps with my UI up, and around 50-70fps without it. Unfortunately the IF bank varies from 5fps while the UI is up, to around 10 when its down, but nothing unusal for a realm with way too many alliance on it ;)

Either way, it's a good starting point. I might fiddle around with my addons and UI settings to see if I can clear it up any more.

edit: Video is an ATI X800 runnin on a 32bit chroot inside Ubuntu for AMD 64 btw.

---

### Post by Gordie on 2005-11-25
Thanks for the reply,

I haven't found anything that really solves this issue, I did lower all my settings to the lowest, and at some points when I have the UI disabled I get a blistering 90fps and the game looks so fast! ;)

I'm runnin a P4 2.4c with 2gig of RAM so I'm pretty sure it's something to do with either the ATI drivers or the way WoW writes the UI to the OpenGL framebuffer... I'm not entirely sure though.

I am using the following command to launch my wow though:

nice -n 19 wine WoW.exe

I don't use the -opengl switch because I've setup the gxApi "OpenGL" in my Config.wtf file inside the WTF folder.

Lemme know if you come across any results in your searches and I'll do the same. ;)

---

### Post by brdweb on 2005-11-25
In response to the UI mods, I would do a search for the 'discord' mods. You can hide / show / tweak just about ANY part of the UI.

I'm running it under cedega for now simply because although I installed it using wine, I didn't feel like compiling the patches in. Performance on my machine is slow, but not much slower than windows. It's a p4 1.7 laptop with only a 32meg geforce card :)

---

### Post by nrwilk on 2005-12-11
The slowdown associated with UI mods in WoW is an issue under all systems.  I had the same issue with my Radeon 9800 Pro (256MB) on my PowerMac G4 dual 1.25Ghz, and also running WoW on an Athlon 3500+ Box with an Nvidia 6600TD (256MB).  Both boxen have 1Gb of ram.  I have no money (being a college student) so I cannot afford Wow until summer, or else I'd be playing RIGHT NOW.  Oh god I miss it.

---

### Post by NickRich on 2006-10-04
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

Read the section about the regedit.

---

### Post by Sp00ne on 2006-10-04
[Curse-gaming.com/en]("http://curse-gaming.com/en")

It's a site with various addons which *could* make you interface smaller = less resources = faster gameplay.

---

