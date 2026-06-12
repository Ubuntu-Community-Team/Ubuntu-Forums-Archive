---
title: "Do not even try to play super nintendo on 14.04"
date: 2016-03-17
forum: Emulators
---

### Post by merockstar on 2016-03-17
Hello,

I'm trying to get an SNES emulator to work in 14.04 and am having issues.

If I can solve any of these three problems, I'm good to go.

Problem 1)
ZSNES freezes every 35 minutes like clockwork. This problem seems to have existed for a long time. I see lots of forums posts in the past about it but no solutions. It's playable, but not actually enjoyable.

Problem 2)
The latest version of snes9x produces the following error when I try to run it:

```
./snes9x-gtk: error while loading shared libraries: libpng14.so.14: cannot open shared object file: No such file or directory
```

Problem 3)
In one version prior to the latest version of snes9x, I am having severe sound distortion issues on a variety of different settings.

I'm thinking about trying still one version of snes9x prior, but I thought I'd see if you guys could think of anything. Here I thought the upgrade to 14.04 had gone flawless, until I tried to play super nintendo :P

I can't use that super fancy super accurate emulator byuu wrote, my computer isn't that great.

Can anybody else offer a solution perhaps that I haven't thought of?

---

### Post by howefield on 2016-03-17
Moved to the "*Emulators*" forum.

---

### Post by merockstar on 2016-03-18
tried higan anyway and experienced a similar sound issue to the one in the previous version of snes9x, I think I'm good if I could get that solved.

I'm about to try upgrading to 15.10, in spite of being an LTS type personality.

---

### Post by merockstar on 2016-03-18
Okay so, ran into a slight hiccup there as my computer crashed in the middle of the upgrade to 15.10. Got it sorted out.

Finally got everything updated, and left zsnes running without using it for an hour to test it because all the other threads on the matter said it would freeze even without a game running. So far so good.

Don't have time to actually test it tonight, but my intuition strongly tells me the problem is solved, so I'm going to mark the post solved, and if I don't come back and bump this post later then please assume it is.

Unless I come back complaining that this didn't work later, I'm going to leave a warning here to anybody who stumbles across this thread who is a super nintendo fan trying to run 14.04: just give it up. I tried everything. I tried playing the game for a couple hours with it crashing, then installing dependencies from rpms to get snes9x latest version to work, tried tinkering with sound for hours in two different programs, tried earlier versions of two different programs, googled every which way my admittedly lacking google fu could muster. If you are averse to upgrading, believe me, I understand. But this time you really need to just spare yourself and bite the bullet if SNES is important enough to warrant upgrade in a worst case scenario.

---

