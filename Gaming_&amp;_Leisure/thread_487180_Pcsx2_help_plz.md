---
title: "Pcsx2 help plz???"
date: 2007-06-28
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-06-28
Ive tried setting up pcsx2 (playstation2 emulator) in the past but still i have had no luck getting it to work,,, could someone plz help me set it up?

---

### Post by yimmmy on 2007-07-01
games for the ps2 emulator are very rare to find  
there are just a few demos that i know of that work

---

### Post by acoustibop on 2007-07-01
Apparently PCSX2 now plays [a number of Playstation 2 games]("http://www.pcsx2.net/compat.php?c=key"), although you'll need a pretty highend machine for acceptable results.

---

### Post by kdarkentity on 2007-07-02
hmm damn...

---

### Post by kdarkentity on 2007-07-02
Is there a Linux compatible Playstation 2 emulator that doesn't require a lot of graphics power to run??

And If so could someone plz tell me how to set it up???

---

### Post by hikaricore on 2007-07-02
Threads merged.
Stop making new threads about the same topic. (this isn't your first time)

Also one question mark is sufficient.

---

### Post by kdarkentity on 2007-07-02
the reason i make new threads is because people sometimes overlook my other ones

---

### Post by hikaricore on 2007-07-02
That's not a valid reason.

---

### Post by kdarkentity on 2007-07-02
what is a good reason to repost than?

---

### Post by Zyphrexi on 2007-10-13
eventually someone interested will find your post, and respond to it. Like I did, when I was searching for info on PS2 emulators.

I know it talked about building from source if you run into problems, and you could always try wine, but I have no knowledge if either would solve your issue.

---

### Post by kdarkentity on 2007-10-13
I have completely abandoned the idea of a ps2 emulator, ive tried to get one to work in both windows and linux and i dont think thats gonna  happen

---

### Post by aphirst on 2007-10-15
I think the idea of a PS2 emulator is fabulous, since my dead PS2 (which I once aptly named "old faithful") fails even to boot these days...
The precompiled pcsx2 binaries from their website worked fine on my Feisty 64 laptop. Well, I say fine, but mean that my BIOS dump looks all spazzed and my rip of FFX fails to play past the point in the New Game intro where it says "Final Fantasy X" (it hangs for a while, then segfaults). Frames per second are immense though.
There's a how-to on [this forum thread]("http://ubuntuforums.org/showthread.php?t=399165&highlight=pcsx2") which compiles it from SVN source, which also "worked" for me. Either way, cd-ing to the directory you installed it in and typing ./pcsx2 normally does the trick for me.

That probably hasn't helped that much, but hey, at least it shows that someone loves pcsx2. *waves exceptionally small flag*

(Of course, I;m sure that *many* people on the forums like the program; but I had to come up with something to finish the post. Otherwise I would ramble on forever. Like I am now... :S )

---

### Post by disturbedite on 2007-10-15
> **aphirst said:**
> Well, I say fine, but mean that my BIOS dump looks all spazzed and my rip of FFX fails to play past the point in the New Game intro where it says "Final Fantasy X" (it hangs for a while, then segfaults).
have you checked the compatibility list to see if it is actually supported?  the reason for it running poorly may not be your rip.

---

### Post by aphirst on 2007-10-16
According to the compatibility list for the most recent release of pcsx2, it is apparantly able to play from start to finish. Is the version for linux the same as the most recent overall?

Also, the BIOS is spazzy for every game (whenever you go through the BIOS menus that is); and the program even segfaults when I try to compress an iso into bz . (but not when i try z :S ). Curious.

Maybe it's a known issue with amd64 Ubuntu (or, more likely, maybe it;s just me :P ); and others can't get it to even display the BIOS properly. I'll also try seeing if re-dumping my BIOS works...

---

### Post by disturbedite on 2007-10-16
if it is fully compatible according to the compatibility list then perhaps it is your rip.  thats all i can think of...

---

### Post by aphirst on 2007-12-29
I re-ripped it from my original DVD. But I downloaded the newest SVN source and now it plays!

The graphics plugin is a bit crappy (artifacts galore; and the skin which cvers eyeballs doesnt always render, so people look like zombies), and it's still in great need of 64bit optimisation, but "YES"!

---

