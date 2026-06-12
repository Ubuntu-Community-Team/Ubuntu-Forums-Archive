---
title: "ZSNES for Ubuntu 9.10"
date: 2009-11-01
forum: Gaming &amp; Leisure
---

### Post by n4q on 2009-11-01
Hey guys I installed Ubuntu 9.10 and I would like to know how I get start playing games with ZSNES. Step by step please, thanks. 

(Insanely new to linux)

---

### Post by shaggy999 on 2009-11-01
Assuming you're using 32-bit karmic just:

sudo apt-get install zsnes

Then go into the games menu, start zsnes and load your favorite rom of choice.

As for 64-bit, that's tricky. It can't be compiled for 64-bit platforms apparently and the only way I was able to do it was downloading a custom deb file of it in a bug report. Forget where I got it exactly.

---

### Post by KIAaze on 2009-11-01
You just need ROMs of the games you want to play. They usually have the extension ".smc".
Then in ZSNES, just load it somewhere in from the menu.

I wanted to try it again right now, unfortunately my new PC is 64-bit and it seems zsnes is not available for 64-bit architectures. :(

---

### Post by ShadowTek on 2009-11-01
They *did* make a working 64bit Ubuntu package for Intrepid, but they've been having some kind of problems uploading a new one.

I didn't try it for Karmic, but I *did* install it on 64bit Jaunty by manually downloading and installing the 64bit Intrepid package.
[http://packages.ubuntu.com/search?keywords=zsnes](http://packages.ubuntu.com/search?keywords=zsnes)

---

### Post by shaggy999 on 2009-11-01
> **ShadowTek said:**
> They *did* make a working 64bit Ubuntu package for Intrepid, but they've been having some kind of problems uploading a new one.

I didn't try it for Karmic, but I *did* install it on 64bit Jaunty by manually downloading and installing the 64bit Intrepid package.
[http://packages.ubuntu.com/search?keywords=zsnes](http://packages.ubuntu.com/search?keywords=zsnes)

This may have been how I got it. Anyway, I can confirm that it works on 64-bit if you have the right package, you just have to hunt and peck for it as it is not in the repos.

---

### Post by KIAaze on 2009-11-01
A little bit off-topic now, but I did get it to work. Thanks for the tips. :)
1) Downloaded and installed the intrepid 64bit version of zsnes: [http://packages.ubuntu.com/intrepid-updates/zsnes](http://packages.ubuntu.com/intrepid-updates/zsnes)
2) Launched zsnes with
```
zsnes -ad sdl
```
to avoid segfault.

cf also: [http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

Only thing not working right now is the sound, but that seems to be a general issue with Kubuntu 9.10 (sound only works in KDE apps)...

---

