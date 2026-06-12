---
title: "Requesting a .deb package (32 and 64-bit) for Vdrift 2009-06-15"
date: 2009-07-30
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2009-07-30
Hello !

I don't make a lot of requests on those forums.
But since it's early versions this game didn't have a Linux package.

If someone can make a .deb or .package for the latest stable version Vdrift 2009-06-15 , it will be great.
Please make the package for 64-bit machines as well.

Link to the game : [http://vdrift.net/](http://vdrift.net/)

Sources : [http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download](http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download)

Thanks ahead.


P.S
I know this game have a .package installer, but it's only for much earlier versions - a lot had changes since then.

---

### Post by KhaaL on 2009-07-31
+1 for this

VDrift is one of the best racing games for linux, why there isnt a deb is beyond me...

---

### Post by binbash on 2009-07-31
+1

---

### Post by Clopin on 2009-07-31
+1. I'd like to be able to play it.

---

### Post by ELD on 2009-07-31
It sure would make things a lot easier.

---

### Post by hhh on 2009-07-31
I got Vdrift running using the instructions for compiling found here...
[http://wiki.vdrift.net/Compiling](http://wiki.vdrift.net/Compiling)

To break it down...

Grab the source...
[http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download](http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download)
Move it to /home/USER

While that's going, open a terminal and copy/paste/enter the following...
```
sudo apt-get install g++ scons libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev libvorbis-dev libglew-dev libasio-dev
```

When the Vdrift source is done downloading...
```
tar jxvf vdrift-2009-06-15-src.tar.bz2
```

and...
```
cd vdrift-2009-06-15
```

Now you get to see what dependencies you're still missing! It takes a long time to build, and has some very long pauses, so be patient. If you get an error, you'll have to start searching for the packages in Synaptic (post the error message(s) so people can help you)...
```
scons release=1
```

If that went through, you should be all right. The wiki says you can run it w/out installing, but I couldn't figure out how. So...
```
sudo scons install prefix=/usr/local
```

And to run it, Alt+F2, enter /usr/local/bin/vdrift, hit run. A terminal starts and you're off.



My thoughts...
Looks are, bleh.

Racing sucks, where's the drifting?

Top speed of what, like 100 in the straights? OOOOooooo, exciting.

Sound, WTF? (To be fair, I get crackling sound in half the games I've tried, perfect sound in the other half.

Nice bug if you go into full screen mode at a lower res than your desktop... that resolution persists after you quit! Bully!

Honestly, what is the fuss? I had more fun playing Cruisin' USA at the arcades in the early '80s. I removed it after 10 minutes, the game is nowhere near ready. Have you seen Burnout Paradise? Not a fair comparison at all, but Holy Crap!

If you want a free game deb, at least make it a fully realized semi-modern game, and a good one, too (install the data deb first, then the other two. Looks great! Fast as hell! Supports gamepads! Happy fragging.)...
[http://www.getdeb.net/app/Nexuiz](http://www.getdeb.net/app/Nexuiz)

---

### Post by mtinman on 2009-08-09
I was working on packaging it with Giftwrap, but as far as know, Giftwrap does not yet support scons, which is the tool used to build vdrift, not automake. I'll keep working on this, and I'll keep you posted on my progress...

---

### Post by MaximB on 2009-08-09
> **mtinman said:**
> I was working on packaging it with Giftwrap, but as far as know, Giftwrap does not yet support scons, which is the tool used to build vdrift, not automake. I'll keep working on this, and I'll keep you posted on my progress...

Thanks a LOT.
You can also try to build it the traditional hard way.
Or you can try for a .package which was in the older versions of Vdrift.

---

### Post by 569874123 on 2009-08-11
[http://www.playdeb.net/updates/VDrift](http://www.playdeb.net/updates/VDrift) 
That version is in playdeb now.

---

### Post by MaximB on 2009-08-11
Thanks.

I am not home right now, can I install that .deb on 64-bit ?

---

### Post by MaximB on 2009-08-11
> **569874123 said:**
> [http://www.playdeb.net/updates/VDrift](http://www.playdeb.net/updates/VDrift) 
That version is in playdeb now.


Thanks a LOT

Excellent, the game is working on 64-bit !

---

### Post by realzippy on 2009-08-11
"could not find package vdrift"

is what I get.Is it because I am on 8.10 ?

**YES** 
(did not see that 9.04 ;-))

---

### Post by MaximB on 2009-08-11
> **realzippy said:**
> "could not find package vdrift"

is what I get.Is it because I am on 8.10 ?

**YES** 
(did not see that 9.04 ;-))


You need to install playdeb package first.

---

### Post by realzippy on 2009-08-12
> **MaximB said:**
> You need to install playdeb package first.


..got the source and compiled it.It runs but looks kind of ugly...

---

### Post by mtinman on 2009-08-16
I installed & tried it on my 64-bit jaunty, and it appears to work, but mine refused to shutdown without logging out, despite several attempts trying to just kill the vdrift process. Anyway, yeah, it works in game (so far)...

---

### Post by mtinman on 2009-08-16
> **realzippy said:**
> ..got the source and compiled it.It runs but looks kind of ugly...

Yeah, I agree, I was looking forward to those nice looking analog gauges, and I get a digital graph type guage, what's up with that???:confused:

---

