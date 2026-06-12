---
title: "Games that run perfect or near perfect in Wine..."
date: 2006-07-26
forum: Gaming &amp; Leisure
---

### Post by Footissimo on 2006-07-26
Not sure if this has been done..and before anyone says it, yes I know there is the Wine DB, but I'd like to know what games people have got to run reeeally well in Wine (not Cedega) with Dapper.

My games (in Wine 0.9.16):

Jedi Academy - only annoyance is the green screen thing when returning back to desktop
Ameican Mcgee's Alice - aside from green screen, works lovely
Homeworld & Cataclysm - had to adjust the resolutions to desktop to get it working, but aside from that, perfect.

Edit: if anyone else is plagued by the green screen thing - I get 'around' it by having a launcher in the top panel that when clicked just runs a simple script with:```
#!/bin/sh

killall gnome-panel
killall nautilus
```

..in it - just refreshes the desktop and saves clicking around getting rid of the green stuff.

---

### Post by ZylGadis on 2006-07-27
Hey Footissimo,
Add Divine Divinity to the list - works perfectly, as long as you apply the correct no-cd crack. I've only tried version 1.0. There are patches for versions up to 1.34, but specifically 1.34 uses a different kind of copy-protection mechanism, for which no crack works in wine (tried extensively). To be on the safe side, I just left my version at 1.0, although it is very conceivable that anything up to 1.33 will work, too.
As far as the green thing is concerned - I have a twinview desktop at 2560x1024. Divine Divinity runs in 1024x768 on the left monitor. Sometimes it does not switch back to 2560x1024 when it exits, and even if it does, it leaves the green thing. To solve that, I have just added:

xrandr -s 2560x1024

as the last command of my custom divinity.sh script.

---

### Post by Lord Illidan on 2006-07-27
What greenthing? Can anyone show a screenshot of the thing?

As for me, Starcraft worked near perfect..just a little bit too slow for my liking. Same goes for Warcraft 3, where sound tended to stutter or lag.

---

### Post by ZylGadis on 2006-07-27
The "green thing" is generally a mangled desktop that wine leaves behind. As soon as a particular pixel is refreshed, all is good, but not before that. E.g. you can drag a window around so that nautilus refreshes the desktop. Gnome-panel is a bit more problematic (in my case, as it is always on top), so you can just restart it.
Changing the resolution seems to fix all that.
Regarding sound problems, two very quick improvements:
1. Switch wine's sound output to OSS. I can't stress that enough. Wine has problems with ALSA and ESD (I have not tried others, e.g. jack). Switching to OSS (which may be problematic if you have no hardware mixing and use ESD, play music at the time, etc - as those overtake OSS) should solve most of the problem.
2. Start the game by:

nice -18 wine gamefile.exe

That puts a part of wine at a much LOWER priority than anything else running. I'm not very acknowledged with wine's intricacies, but this nice little trick helps wine's performance a lot. Forcing the processor to spend LESS time on a particular part of wine boosts performance. Odd, but it works great.

A possible third trick is to fiddle with wine's configuration and tweak its OSS queue length / buffer size, as that is the main reason for the sound buffer underruns that cause the sound stuttering. I haven't had the need to do that so far.

---

### Post by diepruis on 2006-07-27
I have Warcraft III:TFT working flawlessly, Call Of Duty laggy with bad sound, StarCraft laggy and Dark Reign working perfectly (yes I know, you don't need to say it.)

---

### Post by Carrots171 on 2006-07-27
Look on the Platinum List and Gold List on the [Wine AppDB]("http://appdb.winehq.org/"). You'll find quite a few games there.

---

### Post by Footissimo on 2006-07-27
> **Carrots171 said:**
> Look on the Platinum List and Gold List on the [Wine AppDB]("http://appdb.winehq.org/"). You'll find quite a few games there.

> **Footissimo said:**
> e..and before anyone says it, yes I know there is the Wine DB, 

;)

---

