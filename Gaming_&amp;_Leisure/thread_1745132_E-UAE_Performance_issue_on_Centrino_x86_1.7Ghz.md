---
title: "E-UAE Performance issue on Centrino x86 1.7Ghz"
date: 2011-04-30
forum: Gaming &amp; Leisure
---

### Post by wittzi on 2011-04-30
Hi All,

Having just realised that E-UAE is available on Ubunto I eagerly installed it and tried to load Tetris.  It did so, but the performance is absolutely awful (takes about 4 minutes to load and is really jerky).

I'm on 11.04 (having upgraded today) so I don't know whether it's my hardware or the OS version.  I accept that my laptop isn't breaking any speed records (my i7 running win7 runs WinUAE fine), but having searched around quite a bit I can see that people were playing games fine on their PII 233Mhz machines so I presume my feeble laptop should still have enough 'oomph' to emulate 68000 architecture?

My CPU doesn't get above 50% when it's running and my memory doesn't move above 500Mb (I have 1GB).

I would absolutely love to play my old games on my laptop, so if anyone could either confirm whether it's OS related or hardware related or give me any pointers to get it working if not I'd be hugely grateful!

---

### Post by mips on 2011-05-01
Your hardware seems fine so it's probably something else.

---

### Post by wittzi on 2011-05-01
Thanks mips, although now I'm even more confused I guess.

I've been looking at the E-UAE site and oddly there's not a great deal of information there.  However, the only obvious thing that I could think of would be whether the emulation is not done purely by the CPU and that my GPU driver wasn't working properly, but I've just played Warzone 2100 without any problems so I'm certain that they're ok.

The JIT section is completely greyed out - I wonder if that indicates something?  I'm just gutted as this truly would have been an awesome application to run on my laptop!  I guess I'll keep trying to work out what it is, but being a bit of a noob I'll be struggling!

---

### Post by wittzi on 2011-05-01
Ok I've fixed it.  It was me being a noob (sort of)!

There are two versions in the Ubuntu Software Centre.  If you search for E-UAE you get the wrong one, if you search for Amiga you get two versions; the first one being the correct one.

So for me:

Version 0.8.29-7 (uae) = WIN
Version 0.8.29-WIP4-10 (e-uae) = FAIL

Thanks though mips - you at least made me give up on the hardware angle and try some other avenues!  Now I'm off to see if I can complete Treasure Island Dizzy again ... :P

---

### Post by mips on 2011-05-02
Try some other greats like Turrican II, New Zealand Story, Rainbow Islands, Shadow of the Beast, Speedball II, Wings, Xenon II, Prince of Persia, Syndicate, Civilization, Virus, James Ponde, Fire & Ice, Chaos Engine as well as the Delphine & Lucas Arts adventure games

---

### Post by FrodeSolheim on 2012-05-01
> **wittzi said:**
> Hi All,

Having just realised that E-UAE is available on Ubunto I eagerly installed it and tried to load Tetris.  It did so, but the performance is absolutely awful (takes about 4 minutes to load and is really jerky).
...
I would absolutely love to play my old games on my laptop, so if anyone could either confirm whether it's OS related or hardware related or give me any pointers to get it working if not I'd be hugely grateful!

Hi, I would like to recommend trying FS-UAE, which I'm the author of. It has an updated emulation core from WinUAE, and the video/audio/input layer is rewritten from scratch, so it may work better for you than E-UAE. I run it myself on Ubuntu :)  (just note that with 12.04 and 3D-accelerated desktop, you may need to run FS-UAE in fullscreen or with the option --video-sync=off to get good performance due to a Compiz issue).

If you try it out and have any problems, just let me know.

EDIT: [http://fengestad.no/wp/fs-uae](http://fengestad.no/wp/fs-uae) (I provide precompiled Ubuntu/Debian debs).
[]("http://fengestad.no/wp/fs-uae")

---

