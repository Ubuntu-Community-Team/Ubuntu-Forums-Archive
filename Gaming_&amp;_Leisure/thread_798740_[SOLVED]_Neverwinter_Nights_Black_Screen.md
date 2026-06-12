---
title: "[SOLVED] Neverwinter Nights Black Screen?"
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by Nebelhom on 2008-05-18
Hi guys,

just a quick question. I installed nwn on ubuntu hardy via this guide

[http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

got a black screen but the sound worked fine. I went into nwn.ini and changed resolution from 640x480 to 1280x1024 as I had this problem with resolution on my monitor before.

This worked fine and I was able to get a picture and all.

The second time I started nwn, I get the black screen again, although my nwn.ini is still adjusted.

has anyone of you had this problem before as well? if so any suggestions what to do?

oh prob important: I'm a newbie to linux and the community so easy to follow instructions would be cool. I understand the basics I think, but advanced is too much.

below is my nwn.ini if it helps. thanks guys

Nebelhom

P.S. I swapped height and width values round as well, just in case I was bein daft, but to no avail

```
[Sound Options]
Speaker Type=-1
SoundFX Volume=0.60
Voice Volume=0.95
Music Volume=0.60
2D3D Bias=1.00
Number 3D Voices=8
Number 2D Voices=8
3D Provider=Miles Fast 2D Positional Audio
Environment Effects=0
DisableSound=0
[Display Options]
RefreshRate=0
BitsPerPixels=32
Height=1280
Width=1024
TexturePack=2
FullScreen=1
[Video Options]
EnableSkyboxes=0
CreatureShadowDetail=1
Gamma=1.000000
VideoQualitySetting=2
EnableEnvironmentShadows=1
EnableFastGrass=1
EnableGrass=0
CreatureWindSetting=0
Enable AnisotropicFiltering=0
Enable Truform=0
EnableVisualEffectsHigh=1
NumShadowCastingLights=3
ShinyWater=0
Enable VSync=0
AntiAliasing Mode=0
NumDynamicLights=8
```

---

### Post by Perfect Storm on 2008-05-18
When you entered the game first time, did you changed some options?

---

### Post by Nebelhom on 2008-05-18
no all I did, was follow the instructions.

then I started the game and had the black screen. I found somewhere on the web, that this could be a resolution issue and it could be resoved in the nwn.ini.

then I did what I wrote down...

any ideas?

---

### Post by Nebelhom on 2008-05-19
anyone?

---

### Post by Perfect Storm on 2008-05-19
I don't know, but here's some long shots.

1) See if compiz is interfering
```
metacity --replace
```

2) which card do you have? Is the correct driver in use?

3) Tried with other resolution than the one your prefered.

4) Launch nwn through the terminal and see if it spits out some errors.
```
sh ~/.Games/nwn-launcher.sh
```

---

### Post by Nebelhom on 2008-05-19
hmmm... ok thanks for your suggestions. it works now. maybe you could explain this as well for me.

When I first installed it, I did not fill out the CD key verification cos it was stupid o'clock at night and I was just glad it finished and I can sleep ;).
So on seeing the picture with the CD key, I thought: great I'll do this tomo... that is when I got the black screen.

I tried your suggestions and nothing worked. so as a last resort, I took the copy of the nwn.ini that I had elsewhere on the PC and exchanged it for the one in the folder (note: only the resolutions were different).
I tested if it worked and didn't (that was the expected result). then I changed resolutions again in the nwn.ini and it worked again (?!?).

Now I filled out the CD keys first before going out and so far I went out twice to test whether it would do it again, but so far it is stable.

I just find this strange. did the changing of the resolution maybe change something in the registry file?

Thanks anyhow, for giving me moral support :guitar:

Nebelhom

---

### Post by Nebelhom on 2008-05-19
errrmmm.... this also solved my youtube problem with having no video window as well.

I really would love to know how these things are interconnected

---

### Post by Perfect Storm on 2008-05-19
Is Ubuntu still under influence of metacity --replace?

---

### Post by Nebelhom on 2008-05-19
no, I closed it all by shutting down the terminal.

what does metacity --replace do?

have you got any clue what the issue was? just asking in case I ever have a graphics/resolution issue and it is the same origin.

btw. graphics card is an nvidia 7600GS

---

### Post by Perfect Storm on 2008-05-19
Ubuntu 8.04 comes with compiz by default which do all these cool stuff. It require 3D acc. to run. Though it's still beta and have some bugs in it which sometime interfer with with other applications/games/etc. Especially games have troubles when Compiz is running, so many disable compiz when playing games to get better performance, avoiding not to play full screen etc. etc.

The command
```
metacity --replace
```
will replace compiz with gnomes old metacity engine which doesn't require 3D acc. But more reliable.
To turn compiz on again you do
```
compiz --replace
```

or install fusion-icon from the repo which make it point'n'click in the notify area on your Desktop. (set it to start up in the session option, then it starts everytime when you log on).

By the way you can put these two commands into script you made by following the guide. If you go back to the guide where it says (under Launcher);
**nano ~/.Games/nwn-launcher.sh**

make it say this instead
```
#!/bin/bash
 
metacity --replace & 
cd ~/.Games/nwn                
./nwn
compiz --replace &
```

Then it disable compiz starts nwn, when you exit nwn it turn compiz on again.

---

### Post by Nebelhom on 2008-05-19
Ace! Thanks man! I tried it and it works a treat :). I haven't tried this graphics card with very busy games yet (by busy I mean keeping 50 driders with grease, stinking cloud, delayed blast fireball and various other lovely area effects spells at bay; icewind dale 2 style :guitar: )

so far I only ever played fighters in nwn cos of my old sluggish laptop. this'll defo remedy this :)

Thanks again

Nebelhom

---

