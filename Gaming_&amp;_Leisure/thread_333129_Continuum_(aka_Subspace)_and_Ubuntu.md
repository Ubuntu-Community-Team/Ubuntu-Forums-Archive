---
title: "Continuum (aka Subspace) and Ubuntu"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by Gen2ly on 2007-01-06
**Edit:  These instructions may get the game working for you, but I found out a much better way! And posted it.**

[Howto: Get Continuum (a.k.a. Subspace) to work with Ubuntu.]("http://ubuntuforums.org/showthread.php?p=2018916#post2018916")

Wow I just learned that I can play my favorite game - ever - on my newly installed Ubuntu.  Woot!

For those of you who haven't heard of this game, it's wiki describes it as such:

SubSpace is a two-dimensional space shooter computer game published in 1997 by Virgin Interactive Entertainment (VIE). This freeware game incorporates quasi-realistic zero-friction physics into a massively multiplayer online game.

To let you know how I installed it.  I downloaded wine from the Synaptic Package Manager.  Ran winecfg in the command line at my home directory and didn't change anything.

Then followed the instructions at

[Continuum-wine]("http://wine.getcontinuum.com/development.php") 

They've made a custum Ubuntu deb just follow the instructions.

You can change the screen resolution to whatever you use now and it works perfectly well.  I use 1280x800 and I really like it.

A couple notes for me because, I think, the MacBooks aren't supported well in Ubuntu Edgy.

A game windowed doesn't work.  I have to run it full screen.

Sound doesn't work.  I have an issue with the ALSA drivers
> ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
that I could not figure it out.

I got a libjack warning when doing winecfg, I was able to fix this though I don't remember exactly what I did.  However, I don't believe it has anything to do with getting the sound working???

Just click on the continuum.sh script to run continuum.

OH, and BTW --- POWERBALL RULEZ --- hardmode

---

### Post by axle_foley00 on 2007-01-07
Awesome stuff. I used to love this game. Thanks for the heads up on this. :D

---

### Post by unfun on 2007-01-07
When I come here $ ~/Continuum-wine/continuum.sh    , I get this wine: failed to initialize: /usr/local/lib/wine/ntdll.dll.so: cannot open shared object file: No such file or directory

---

### Post by unfun on 2007-01-07
```
winecfg
```


Under the 'sound' tab, change one of the drop-down boxes (hardware acceleration, I think) to 'emulated'.

Your sound should work now.


Can anyone tell me how to get the game running?

---

### Post by Gen2ly on 2007-01-07
unfun, use the link above.   There's a slightly different version of Continuum for Ubuntu.  If this doesn't work, use Synaptic and mark wine complete removal, then reinstall and try Continuum again.  Just double click on continuum.sh and click. Run.

---

