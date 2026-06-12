---
title: "World of Warcraft FPS - 6.10 edgy"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by shazzed on 2006-11-07
Started this thread to find out who is running WoW on Ubuntu 6.10 edgy or even 6.06. I really want to gauge if it is worth running on Linux at all.

Please post your system specs and OpenGL FPS and or Direct3D FPS

15 -35 fps(Direct3D)

Intel Core Due 1.8 x2
1 gig ram
Nvidia 7950GTX

---

### Post by reiki on 2006-11-07
Wine 0.9.24 and Edgy (Ubuntu 6.10)
nVidia 7300GT 512MB
PentiumD 930 with 2gigs of ram

Standing at the Great Forge in Ironforge
75-80FPS openGL
I don't do this in d3d

---

### Post by shazzed on 2006-11-08
I might ad mine is a default Wine 0.9.24 install
OpenGl is obviously the way to go.
Please ink this thread if you run wow as well.

---

### Post by rejser on 2006-11-08
opengl, wow-compiled wine. Running opengl. 1280*1024, som options high some low.
gf 6200 running ~50-60 fps

---

### Post by Ferrat on 2006-11-08
Wine 0.9.24

1240x1024 with settings at default (some higher)

AMD64 - 3200+ 
1536 DDR RAM
ATi X800 XT PE

Standard FPS is about 25-50FPS
Highest I've had playing 100FPS in BFD
Lowest in Alterac Valley when all 80 ppl was fighting at the Stormpike gates and we where defending the flag and both sides did lots and lots of AoE spells. 8-20FPS 
But it was still playable (it sounds weird I know) but even at 8FPS by some reason in Linux (for me atleast) it still had flow, in windows when you get low FPS you can't control **** and in PvP your dead meat but not the case here.

---

### Post by shazzed on 2006-11-08
> **rejser said:**
> opengl, wow-compiled wine. Running opengl. 1280*1024, som options high some low.
gf 6200 running ~50-60 fps

Damn that isn't bad for a 6200 at that res !

Ferrat:
Hopefully ATI will pull their finger out and release real drivers not the slapped together ones they have. I predict with UT2007 (Linux client supported) they will have to or lose sales.

So I checked out Transgameing and got Cedega, installed and got better frames but nothing to compare to my system specs. What a waste of money that was!

I suck at linux and can't seem to compile Wine with the nvidia patch ](*,) . If anyone could link me a WoW patched Wine 0.9.24 for Edgy that would be sweet. I really want to ditch windows!

---

### Post by shazzed on 2006-11-08
Ok so I looked I bit harder.
[http://www.ubuntuforums.org/showthread.php?t=290761](http://www.ubuntuforums.org/showthread.php?t=290761)


After I do the simple install of wine 0.9.24  from winehq or [www.getautomatic.com](www.getautomatic.com) (installs latest wine).

If I just get the patched winex11.drv.so from:
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
and place in my "/usr/lib/wine/"

Then simply change the wow.cfg so it runs in opengl I should be set ???

Keep the FPS coming btw. Would be interested to see more ATI improvements.

---

### Post by graigsmith on 2006-11-08
ati 9200 using open source drivers.  latest wine from edgy's repositories.

i was getting 10-30 in high traffic areas, or heavy raiding areas, in general 25-30 fps in most situations.  in low traffic areas it sometimes went up to the high 50's.

overall it was very playable.  even on a very slow by today's standards ati 9200.  

i run it in a window at around 800x600.  though sometimes i maximize it, but only loose a couple of fps by maximising it.

i actually just stopped paying, because i am getting tired of the game.  plus the wii is coming out this month. ooooh :)

---

### Post by reiki on 2006-11-08
> **shazzed said:**
> Ok so I looked I bit harder.
[http://www.ubuntuforums.org/showthread.php?t=290761](http://www.ubuntuforums.org/showthread.php?t=290761)


After I do the simple install of wine 0.9.24  from winehq or [www.getautomatic.com](www.getautomatic.com) (installs latest wine).

If I just get the patched winex11.drv.so from:
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
and place in my "/usr/lib/wine/"

Then simply change the wow.cfg so it runs in opengl I should be set ???

Keep the FPS coming btw. Would be interested to see more ATI improvements.

Shazzed-

What you see in that post is what I've done and it works. That patched binary was to take care of a flickering video problem with nVidia cards. If you look at the site, 
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
you'll also see mention pretty near the top about a regedit that benefits ATI and I can tell you it benefits nVidia as well. It just about doubled my frame rate.

---

### Post by shazzed on 2006-11-08
I missed that little bit at the bottom! 100% hot damn!
Seen the ATI and just ignored it.
Will give it a go tonight and report back. I plan to do a fresh install after I have seen some aceptable frame rates.
Thanks reiki

---

### Post by Amurko on 2006-12-02
System 1:

Core 2 2.4 Ghz, 1Gb DDR2-533 RAM, Geforce 7600 256 MB RAM PCI-e, Ubuntu Edgy 64-bit edition

a) Using Cedega: FPS = 60 - 120
b) Using Wine: FPS = 30 - 60

System 2:

Pentium 4 2.4Ghz, 1 GB DDR 3200 RAM, Geforce 4 440 MX (w/ 128 MB RAM, AGP), Ubuntu Edgy

a) Using Cedega: FPS = 20 - 70
b) Using Wine: FPS = 5 - 20

---

