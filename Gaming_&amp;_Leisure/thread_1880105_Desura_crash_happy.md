---
title: "Desura crash happy?"
date: 2011-11-12
forum: Gaming &amp; Leisure
---

### Post by weasel fierce on 2011-11-12
Been messing around with Desura and it's pretty neat but.. the client seems extremely crash happy. Often it'll crash without any warning whatsoever, while downloading something.

Im on 64 bit Kubuntu 11.10. Any idea what gives?

---

### Post by Perfect Storm on 2011-11-13
Haven't crash for me yet.

But try 'Desura force', it may that you haven't received any updates.

Otherwise run desura in konsole and it may give away what's happening.

---

### Post by weasel fierce on 2011-11-13
No error when it disappears.

It does give me this when I run it

[1112/224434:WARNING:plugin_lib_posix.cc(113)] /usr/lib/flashplugin-installer/libflashplayer.so is nspluginwrapper wrapping a plugin for a different architecture; it will work better if you instead use a native plugin.

Im not sure if that's actually the cause though or not.

---

### Post by Perfect Storm on 2011-11-13
Try install flash 64-bit instead of running flash 32-bit with nspluginwrapper.

---

### Post by weasel fierce on 2011-11-13
Im an idiot :)

Somehow I never noticed that it was 32 bit flash. I wonder if that's the default somehow. 

I updated it, and I'll see how it goes.

Thanks for letting me bounce it off of you comrade


It crashed again, but it seemed to run longer at least. We'll see what happens.

---

### Post by lodle on 2011-11-14
Hey,

Im the developer of Desura and im trying to stamp out crashes as fast as i can. That warning hasnt been in the build for over 3 weeks now make sure your running the newest build (build 21 i think) and also that your running the correct bit version.

Mark

---

### Post by weasel fierce on 2011-11-14
It updated yesterday, and now it's been running overnight and didn't bug out, so I think we're good.

Very pleased by the software btw.

---

### Post by Perfect Storm on 2011-11-14
> **weasel fierce said:**
> 
Very pleased by the software btw.

+1

Suggestion: filtering the games after OS would be nice on Desura.

---

### Post by lodle on 2011-11-14
Looking at open sourcing Desura in the coming weeks so hope this will invoke some community improvement that i dont have time to do.

---

### Post by em3raldxiii on 2012-11-20
> **lodle said:**
> Looking at open sourcing Desura in the coming weeks so hope this will invoke some community improvement that i dont have time to do.

Wow, I really applaud you for considering going open source.

I have been having some strange issues with Desura recently ... the update hasn't been "sticking".  I fire up Desura, run a game, and then at some point it just closes with no fanfare (both the game and Desura simultaneously).  I haven't run it from CLI yet, but I get the "ln: failed to create symbolic link `../lib/libgconf-2.so.4': File exists" warning now, and I am not sure when that started.  I'll try running Desura from CLI and maybe post some debug info.  My system is relatively stock, and I haven't muddled too much with anything that should affect these things, so I am sure you will want to see what the issue is all about.

Anyhoo, great work on a great platform.  Cheers!

---

