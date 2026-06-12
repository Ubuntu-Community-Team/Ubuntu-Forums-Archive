---
title: "sdlmame and compatible ROM's"
date: 2009-10-14
forum: Gaming &amp; Leisure
---

### Post by Jaraxle on 2009-10-14
After some frustration, I managed to get sdlmame running. I can run games from the command line and I also have WahCade working. My problem is that almost none of my ROM's work anymore. (I am using sdlmame 0.13).

I have searched a great deal and have found out that this is a common problem. As time goes on, newer ROM's are developed, etc. My question is this: how do I find a working set of ROM's? Is it simply the most current ROM's (by date)? Or is it specific to your emulator, ex. sdlmame 0.12, sdlmame 0.13, etc.?

I'm not looking for anyone to tell me where to find ROM's, just what I should be looking for. I remember now that I once had this problem in Windows as well. So once I get a working set of ROM's again, I'm not going to change my version of MAME again! :)

---

### Post by hikaricore on 2009-10-14
The problem is often with regressions in the emulator itself and has nothing to do with the rom.

I had an issue with UMK3 which was resolved by reverting to v0.123.
You can find older versions here: [http://sdlmame4ubuntu.org/old/](http://sdlmame4ubuntu.org/old/) and the newest release here [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/).

I'll try and attach 0.123 to this post to see if it can help you as it did me.  :p

[http://www.mediafire.com/file/luwmdnzwmnt/sdlmame_0.123-0ubuntu1_i386.deb](http://www.mediafire.com/file/luwmdnzwmnt/sdlmame_0.123-0ubuntu1_i386.deb)
[http://www.mediafire.com/file/zzznjzzamdm/sdlmame-tools_0.123-0ubuntu1_i386.deb](http://www.mediafire.com/file/zzznjzzamdm/sdlmame-tools_0.123-0ubuntu1_i386.deb)

These packages may require older libraries and some clever hacking to get working, but this exact version solved all my troubles. :p
Best of luck.

---

### Post by disturbedite on 2009-10-14
no ROMs are not "developed". the emulator is (as hikaricore said).

telling you how to find them may be just as much of a violation of the rules as telling you where to find them.

---

### Post by Jaraxle on 2009-10-14
I had downloaded the newest release from wallyweek.org. Something told me I should have downloaded version 0.12, I normally try to avoid the very latest version of software.

I'll try to install the .deb package you provided but I might not be able to figure it out if it has certain dependencies. I'm not sure what libraries sdlmame uses although I did see some libsdl* packages being used in Synaptic.

---

### Post by Melcar on 2009-10-14
[http://sdlmame.wallyweek.org/]("http://sdlmame.wallyweek.org/")

All of my ROMS work with 0.127.  Newer versions don't recognize some of the ROMs (usually the NEO-GEO ones).  Just install the packages; Synaptic may complain about a newer version being available but it's safe to install anyway.

---

### Post by Jaraxle on 2009-10-14
Yep, it's working! I have 0.123 installed and all my ROM's are working. Synaptic did prompt me to keep the newer version but I used selected package instead and it installed with no trouble.

Thanks for pointing me in the right direction!

---

### Post by Melcar on 2009-10-14
Make sure to lock the version otherwise Synaptic will keep bugging you to update the package (and so when doing a system wide update you don't "accidentally" update sdlmame too).

---

### Post by hikaricore on 2009-10-15
The worst thing is that this shouldn't even be an issue.
Basically what happens is the emu refuses to run what it considers and "incomplete" rom.
This regression has been long standing and you'd think it would have been resolved by now.
Several rom lists contained within the emu are flat out wrong after 0.123.
Oh well a solution is a solution anyway.  :p

---

### Post by Jaraxle on 2009-10-15
Cool. I didn't know you could lock a version of software in Synaptic. I did a search for how to do it. Learned something new.

---

### Post by disturbedite on 2009-10-15
> **hikaricore said:**
> The worst thing is that this shouldn't even be an issue.
Basically what happens is the emu refuses to run what it considers and "incomplete" rom.
This regression has been long standing and you'd think it would have been resolved by now.
Several rom lists contained within the emu are flat out wrong after 0.123.
Oh well a solution is a solution anyway.  :p

what? it has always been that way. it is the nature of the emulation & rom dumping scene. newer versions of emulators emulate things in different ways and roms are redumped for various reasons. thats like saying a problem is that dogs bark. well yeah, they've always barked and they won't be stopped from barking.

---

### Post by hikaricore on 2009-10-15
> **disturbedite said:**
> what? it has always been that way. it is the nature of the emulation & rom dumping scene. newer versions of emulators emulate things in different ways and roms are redumped for various reasons. thats like saying a problem is that dogs bark. well yeah, they've always barked and they won't be stopped from barking.

The game shouldn't require a redump in most cases unless there were hacks used for parts that were inaccessible.
How hard is it to maintain backwards compatibility for more than one file set?  Not hard at all.

---

### Post by disturbedite on 2009-10-16
> **hikaricore said:**
> The game shouldn't require a redump in most cases unless there were hacks used for parts that were inaccessible.
How hard is it to maintain backwards compatibility for more than one file set?  Not hard at all.

you don't understand why games are dumped or their nature. some times they are dumped incomplete and not all roms are able to be dumped for various reasons, hence in the future redumps are needed. this is just one example of why.

---

### Post by hikaricore on 2009-10-16
You quoted me without reading what I said... I know a lot about game dumps thanks.

> **The game shouldn't require a redump in most cases unless there were hacks used for parts that were inaccessible.**

In the case of UMK3 there has been no redump however the current versions of sdlmame refuse to use the old file list and now expect a rearranged version which does not exist as far as I've been able to tell.

---

