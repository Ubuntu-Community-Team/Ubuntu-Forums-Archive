---
title: "Alien Arena 7.31 released!"
date: 2009-10-08
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2009-10-08
Version 7.31 of Alien Arena has been released today for windows and linux users! In addition to some exciting new content, there are also a number of engine improvements, optimizations, and gameplay enhancements.

Some of the new features in this release:

[list]
[*]Improved shadow volumes with self shadowing. 
[*]Vertex buffer object management. 
[*]Sound improvements/bugfixes. 
[*]Security fixes. 
[*]Anisitropic image filtering. 
[*]New weather effects. 
[*]Callvoting. 
[*]Duplicate player renaming. 
[*]Two new levels. 
[*]Auto detection of settings on first run. 
[*]Run time optimizations.
[/list]

For a complete changelog look [http://icculus.org/alienarena/changelogs/7.31.txt](http://icculus.org/alienarena/changelogs/7.31.txt)

Alien Arena is open source, free to play, and sets a new standard in freeware FPS gaming. To download the game(windows or linux), or for more information, screenshots and videos, visit [http://red.planetarena.org](http://red.planetarena.org) 

[[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_25_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_25.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_26_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_26.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_23_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_23.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4.jpg)

---

### Post by Melcar on 2009-10-08
Nice.  Downloading right now.

---

### Post by Irritant on 2009-10-10
Lemme know how it works with the autodetection of video settings on first run.  I was hesitant to do this before, and we always just set the defaults to a low level hoping that people would turn them up if they had nice rigs.  Now it is hoping that people will turn them down if they aren't getting good performance, though the detection should give them an appropriate setting for their GPU.  I think most games do this now, and it was time we implemented it.  There were too many people firing the game up, and never seeing what it could look like on higher settings because they didn't even bother, even when they had the GPU for it.

---

### Post by Melcar on 2009-10-10
The game started at high settings for me, but in a 640x480 window.

---

### Post by Irritant on 2009-10-11
Hmmm that's odd that it started in that window size, shoulda been 1024x768.  I'll look into that.  Thanks!

---

### Post by Carpentr on 2009-10-12
Nice graphics as always.   I look forward to playing it. I'm sure it will be just as fun, if not more, than the older versions. Keep up the good work.

---

### Post by Irritant on 2009-10-12
> **Carpentr said:**
> Nice graphics as always.   I look forward to playing it. I'm sure it will be just as fun, if not more, than the older versions. Keep up the good work.

Thanks :)  Got some more stuff in the pipeline for the next release underway already...

---

### Post by Irritant on 2009-10-15
7.32 will be released in a few days.  We discovered that using the Nvidia 191.xx drivers completely blow the game up.  Also, the automatic video settings on first run were causing problems for way too many people.  So with these fixes, plus some new things, we'll have a release out shortly, as well as patch for those with 7.31

---

### Post by benjamimgois on 2009-10-17
When i execute ./crx i receive this message:

./crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory


I'm running Karmic 64bit, Anyone know how to fix it ?

---

### Post by Perfect Storm on 2009-10-17
Try:
```
sh -c "cd <path> && ./crx"
```

---

### Post by what, what? on 2009-10-17
i downloaded the .zip file for the game, does anybody know what i need to do now?

---

### Post by Skwerly on 2009-10-17
Yea, I saw this at a buddy's house and thought WOW!  It looks as good if not better than Halo :).  

Sweet game!

---

### Post by Perfect Storm on 2009-10-17
> **what, what? said:**
> i downloaded the .zip file for the game, does anybody know what i need to do now?

Guide, though it might need a little update: [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)

---

### Post by what, what? on 2009-10-17
> **Artificial Intelligence said:**
> Guide, though it might need a little update: [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)

ok, and i have alien arena on the linux mint part of my computer too but i downloaded AA a few months ago so its not up to date, is there a way to update it without having to download the zip file and wait another 2-3 hours and go through the whole process again? 
(i know it doesnt make sense to have AA on both parts)

---

### Post by spoons on 2009-10-17
Irritant, do you think hardware tessalation support would improve the lower poly models? It's supported on ATi hardware so far, I don't think Nvidia have many/any cards that can do it yet.

---

### Post by benjamimgois on 2009-10-17
> **Artificial Intelligence said:**
> Try:
```
sh -c "cd <path> && ./crx"
```

Artificial Intelligence, i type the command that you suggest, but i receive exactly the same message. Any other sugggestion ?

---

### Post by Enigmapond on 2009-10-17
This game is great with one problem. Everything works well for me except there is no sound. I opened the console and it states no sound source found. Graphics and all else work very well...and fast but the sound problem I have is a bummer....any suggestion?

---

### Post by Perfect Storm on 2009-10-18
> **benjamimgois said:**
> Artificial Intelligence, i type the command that you suggest, but i receive exactly the same message. Any other sugggestion ?

Then try this:
```
sudo apt-get install libxxf86dga1
```

---

### Post by Enigmapond on 2009-10-18
I did and it states newest version already installed....

---

### Post by CheatCat on 2009-10-18
Sometimes the game crashes and I get this error:

```
Received signal 11, exiting...
```

Please help! :(

---

### Post by myromance123 on 2009-10-18
Looks awesome!
  Can't wait to try it out with mah new screen :P

Downloading now! :D

---

### Post by benjamimgois on 2009-10-18
> **Artificial Intelligence said:**
> Then try this:
```
sudo apt-get install libxxf86dga1
```

The package libxxf86dga1 is already installed, maybe it's a problem with the 64bit system.

---

### Post by Perfect Storm on 2009-10-18
> **benjamimgois said:**
> The package libxxf86dga1 is already installed, maybe it's a problem with the 64bit system.

Try compile it instead, or use getlibs to install it.
Also try running **ldd** on the binary.

---

### Post by what, what? on 2009-10-22
> **Artificial Intelligence said:**
> Guide, though it might need a little update: [http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena)

i tried it, didnt work.

---

### Post by Perfect Storm on 2009-10-23
> **what, what? said:**
> i tried it, didnt work.

Where/what didn't work. If you post the input/output, you can get help (hopefully) to fix it.

---

### Post by what, what? on 2009-10-24
well i decided to do it the easy way with playdeb.net
and now i have a problem with it.
instead of it going to fullscreen, its windowed. as shown in the screenshot below:

[IMG]http://img98.imageshack.us/img98/599/screenshot2600x400.png[/IMG]
Does anybody know how to fix this?

And why does it say CRX?

---

### Post by benjamimgois on 2009-10-24
It finally work using the Playdeb PPA.

---

### Post by Irritant on 2009-10-24
> **benjamimgois said:**
> It finally work using the Playdeb PPA.

What version do they have there?  Version 7.32 is currently the latest released version.

---

### Post by benjamimgois on 2009-10-24
> **Irritant said:**
> What version do they have there?  Version 7.32 is currently the latest released version.

Yep, 7.32 is already there.

---

### Post by Irritant on 2009-10-25
> **benjamimgois said:**
> Yep, 7.32 is already there.

Awesome!  If there are any problems please report, we are always trying to make it easier on players in every way.  In fact even today, all rainy and nothing to do, I found another optimization to speed it all up :D

---

### Post by mick@zendo on 2009-10-25
How do I upgrade the version I have installed (7.0) ?
I already downloaded and unzipped but cannot get crx.exe to run
cheers

---

