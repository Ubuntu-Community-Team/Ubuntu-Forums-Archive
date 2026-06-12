---
title: "Quake 2 for GNU/Linux?"
date: 2007-01-30
forum: Gaming &amp; Leisure
---

### Post by Fibonacci on 2007-01-30
Hello,

Just installed the quake2 package from the repos, and tried to run it using the data files from an old Windows install.
First I got an error about /dev/dsp being busy at the time, so I tried aoss quake2.
Then I kept getting this error:
```
------- Loading ref_soft.so -------
LoadLibrary("ref_soft.so")
svgalib: Cannot get I/O permissions.
```
chmod'ing u+s the quake2 executable did not solve the problem (besides, one shouldn't run any game as root in the first place - the root account is there for a reason). After an hour or so of googling, I ran it on the first virtual console.
Oh, my poor eardrums! There was no sound, only high-pitched noise! So I quit the game, find out my virtual consoles are displaying only garbage, but manage to run the game without aoss anyway. So now I'm playing a mute Quake in which I cannot turn left or right because the controls don't work as they're supposed to, and the mouse stops working after trying to change them.

I finally gave up on that approach, and instead tried running the old Windows install with WINE. Well, guess what, it worked flawlessly, sound and everything! The movement is even smoother than on the native version! I guess I'll remove the quake2 package and stick with this.

But, seriously, is there any way of making the native version work? (at least not screwing up the virtual consoles would be fine)

-Fibo

---

### Post by Zyphrexi on 2007-02-10
i have the same problem

---

