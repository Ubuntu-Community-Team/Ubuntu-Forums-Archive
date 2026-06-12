---
title: "PS2 -&gt; USB game pad adapters"
date: 2010-01-12
forum: Gaming &amp; Leisure
---

### Post by papashou on 2010-01-12
Hey,  I've been digging around for some quality PS2 gamepad to USB convertors.  A majority of them seem to come bundled with drivers for Windows, and not much mention on its compatibility with Linux. 

I'm wondering if anyone could recommend a brand/type adapter that works great with Ubuntu, and more importantly, I suppose, is where can I get one? (reliably) Most of the ones I've come across seem somewhat less than legit.

---

### Post by virusiidx on 2010-01-12
I currently have the Super Dual Box Pro, though I haven't used it since Jaunty. It worked well right out of the box of course and I used jscalibrator from the repos to calibrate and configure it. However, I don't see it in the Karmic repos. So not sure what happened to it. But it works without it as well. 

Bought it off ebay for like $10~ish.

---

### Post by papashou on 2010-01-13
Is it this product? (attached)

---

### Post by bvanaerde on 2010-01-13
That's the one I received yesterday... bought it off eBay for about 10 euros. They are a lot cheaper when you buy it from a HongKong seller, but I fear for extra shipping fees.

I have yet to try it though.

---

### Post by OliW on 2010-01-13
> **papashou said:**
> Is it this product? (attached)

That looks like the one I have now. Just plug it in and calibrate with jscal and it should work.

I think they all work pretty much the same because this is my second (lost the first) and it works just the same.

---

### Post by bvanaerde on 2010-01-13
> **OliW said:**
> Just plug it in and calibrate with jscal and it should work.
What about force feedback: does that work too?

---

### Post by OliW on 2010-01-13
> **bvanaerde said:**
> What about force feedback: does that work too?

I haven't tried TBH. I didn't even know there were any games in Linux that supported force-feedback.

---

### Post by bvanaerde on 2010-01-13
> **OliW said:**
> I haven't tried TBH. I didn't even know there were any games in Linux that supported force-feedback.
Not sure about that myself :D But it's written in the manual that it supports force feedback (on Windows), so my guess is that it is used for something...

---

### Post by virusiidx on 2010-01-13
It supported force feedback on some of the games I played in WINE, but I usually disable it.

---

### Post by dfreer on 2010-01-13
I prefer Logitech's gamepads; same button/design layout as the PS2 and it's a native USB device (plug and play no drivers needed). The dual action is the model I have, nice and cheap. I've heard complaints about it but out of the 3 that I have had for 2+ years I haven't had a single issue. There is also a couple more advanced models that come with force feedback, whether the force feedback works in linux or not IDK.

---

### Post by mister_playboy on 2010-01-14
I use one similar to this.  Plug and play on anything (even Windows 2000) and has the added benefit of working with a PS3.

[http://www.amazon.com/PS2-PS3-Playstation-Controller-Adapter-Converter/dp/B0027B475O/ref=pd_sim_dbs_vg_3](http://www.amazon.com/PS2-PS3-Playstation-Controller-Adapter-Converter/dp/B0027B475O/ref=pd_sim_dbs_vg_3)

Logitec's controllers don't measure up to a real PS2 controller, IMO.

---

### Post by doorknob60 on 2010-01-17
I got a cheap genericish one from somewhere (don't remember where though) and it works just fine with Linux and Windows with no extra drivers or software. I think most will work like that.

---

### Post by ShadowTek on 2010-08-16
I bought this one for $1 from seller _366open_ on ebay.

[IMG]http://img5.imageshack.us/img5/8892/tb460bc.jpg[/IMG]

All the buttons and both analogs of my PS2 controller work, but the forcefeedback isn't being recognized by ffcfstress or ffmvforce, even though this adapter *is* listed as supporting forefeedback.

```
:~$ ffcfstress -d /dev/input/js0
ERROR: can not get key bits (Invalid argument) [ffcfstress.c:118]

``````
:~$ ffmvforce /dev/input/js0 
ffmvforce: test orientation of forces
Click in the window to generate a force whose direction will be the position
of your mouse relatively to the center of the window
USE WITH CARE !!! HOLD STRONGLY YOUR WHEEL OR JOYSTICK TO PREVENT DAMAGES
To run this program, run it with at least one argument.

mouse: 332 109 n: 0.66 -0.46 angle: 0.97
level: 547a direction: a768
Play effect: Invalid argument
```I'd like to get it working if someone knows what the problem might be. I read that forefeedback support *is* included with the kernel since Ubuntu 9.04, and I'm currently using 10.04.

---

