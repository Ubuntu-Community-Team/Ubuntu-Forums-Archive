---
title: "UT 2004 sound problem"
date: 2009-08-21
forum: Gaming &amp; Leisure
---

### Post by RayvenSwan on 2009-08-21
I'm still very new to Ubuntu, but managed to get UT 2004 installed and running well... Except the sound. I can't seem to get any whatsoever, have tried a whole bunch of various fixes to no effect except making me tired and grouchy. I get this when running it in the Terminal...
open /dev/[sound/]dsp: No such file or directory
I can honestly say I have no idea what it means really... I mainly just follow guides and copy/paste commands, but that doesn't seem to be working in this case. Could really use some help.

---

### Post by automaton26 on 2009-08-21
I use Kubuntu x64 Jaunty (9.4) and UT2004 sounds worked OK out of the box, although *only* on the first run after a reboot. If I run it again, there's often no sound.

Does sound work for everything else - desktop games, youtube videos, audacity etc.?

And have you installed the final 3369 patch for UT2004?

---

### Post by RayvenSwan on 2009-08-21
Yes, the sounds works quite well on everything else. 
And no, I haven't installed the patch... Which seems like a really obvious thing to do. The only help I saw for that, wasn't. I'll try searching that though.

---

### Post by u235sentinel on 2009-08-21
> **RayvenSwan said:**
> Yes, the sounds works quite well on everything else. 
And no, I haven't installed the patch... Which seems like a really obvious thing to do. The only help I saw for that, wasn't. I'll try searching that though.

I would install the patch and see if that helps.  I had a few problems with UT2004 until I patched it up.  Afterwards it's been rock solid and quite the pleasure to play :D

I ended up buying a few more copies for my kids computers.  It's a lot of fun at our lan parties :D

---

### Post by RayvenSwan on 2009-08-22
After messing with it even more, and extracting the patch directly into the install folder...
I've concluded I have no idea how to install the patch either. #-o
I have tried the Loki(?) installers, they seem to think I haven't installed the game, or that I don't have the disk.

---

### Post by joeelmex on 2009-08-22
go to this web site and follow the guide.. 

[http://gwos.org/doku.php/guides:start](http://gwos.org/doku.php/guides:start)

---

### Post by RayvenSwan on 2009-08-22
Okay, I got it patched with that guide. Thanks.
The problem with the sound however, is still there. 
Same error, I can play and do everything in game, but there's no sound whatsoever. 
I did think of one thing.
I have a Microsoft USB headset, and no sound card. 
Perhaps it needs an actual sound card? 
I kind of doubt that, being as every other sound on the system is fine, just the game is having trouble.

---

### Post by automaton26 on 2009-08-24
In UT2004, there's a config screen for Audio - I think there's a "Software" option somewhere (or OpenAL ?) so try changing that.

Also check the volume levels while you're there (sorry if that's *too* obvious!).

Plus, only test those changes after a reboot - like I said earlier, my UT2004 sound doesn't work on subsequent runs.

---

### Post by PureLoneWolf on 2009-08-24
I had this problem myself

You need to delete openal.so from the UT2004 directory, then use the following command:

```
ln --symbolic /usr/lib/libopenal.so /path/to/ut2004/System/openal.so
```

The libopenal.so should already be a link to the latest version installed on your computer iirc.

Give that a try

---

### Post by RayvenSwan on 2009-08-25
WOO! PureLoneWolf, your fix worked. The sound is working just fine. Thank you so much. :)
... However... 
I can't seem to connect to any online games... 
](*,) It's going to be one of THOSE programs isn't it?

Eh heh heh... Um, upon running it with the sudo command, I connect just fine. So, it's all good now. Thanks people, you've all been really helpful.

---

### Post by vImTo on 2009-11-11
Hi All,

I too have a UT2004 sound problem with 9.10. I had no sound at all, but then followed step by step the (very good) guide at

[http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

I now have sound in the menus fine, but in game it goes all static and distorted to the point it is just noise. When I come back to the menu it recovers.

Does anybody have any idea where I should start looking. ?

Thanks, 
Vim

---

### Post by Perfect Storm on 2009-11-11
Have you tried PureloneWolf's suggestion?


or maybe try this: [http://ubuntuforums.org/showthread.php?t=1309656](http://ubuntuforums.org/showthread.php?t=1309656)


Another option is trying to change audio engine (default pulse audio), to another one. There should be quite alot of thread subjects on how you do it.

---

