---
title: "What would cause a laptop to randomly power off??"
date: 2007-12-04
forum: Dell  Ubuntu Support
---

### Post by inchaos on 2007-12-04
So twice now my laptop has randomly powered down for no apparent reason while I've been surfing the web.

The first time it happened, I searched the forums and concluded that my laptop had overheated.  I installed the sensors applet to monitor my CPU temperatures.  My fan works and it comes on and shuts off periodically as one would expect.  My CPU temperatures have averaged from 30 degrees Celsius in a cooler room to 42 degrees in a warmer room.  If I'm doing something that is CPU intensive like watching a fullscreen video or playing a game, it may get up to 48 degrees.

I thought the problem was a fluke.  It had only happened the one time and I had yet to observe alarming CPU temperatures at any point.

Then this morning:  my comp had been in suspend mode for a couple of hours.  I woke it up.  I was checking my email and had just started typing a reply when out of nowhere comes the terrifyingly ugly noise telling me the power had just been cut.  My CPU temp was 36 degrees Celsius.  

Note: Both times my laptop was on battery power but my battery is nowhere near exhausted.  It was around 80% the first time and around 30% the second time.  After each occurrence the laptop booted without a hitch.

So, my questions are these:

1. What, aside from overheating, would cause my comp to cut power for no apparent reason?

2. What logs can I check to see if there is any report of an error?

3. Is there a possibility I could have a power supply or other serious hardware issue?

My battery is seated correctly, nothing is blocking the fan, my CPU temps seem normal.

What gives?

---

### Post by inchaos on 2007-12-04
UPDATE:

I checked my system log, there are no errors of any kind.  The last messages before the power off were about my wireless network connection.  The messages before that were all from returning from suspend.


Note:  My computer isn't shutting itself down, as in going through the shut down sequence.  Instead, it's powering off with no warning, as if I had held down the power button for four seconds to force a power off.

---

### Post by sr20ve on 2007-12-04
Sounds to me like a hardware issue, possible power supply/distribution board or motherboard.

Is your laptop still under warranty? If so, I'd call Dell support.

---

### Post by inchaos on 2007-12-04
Yeah, I've had it less than six months.

I'm just concerned with it being a non-Windows system that they'll give me a bunch of crap about how it might be OS related.  I'll give them a jingle and see what happens.

Per this thread: [http://ubuntuforums.org/showthread.php?t=631404](http://ubuntuforums.org/showthread.php?t=631404)
I realized it might also be a RAM issue.  I'm going to run a memtest and see what happens.

---

### Post by sr20ve on 2007-12-04
> **inchaos said:**
> 
I realized it might also be a RAM issue.  I'm going to run a memtest and see what happens.

I can almost guarantee memtest will give you errors, and those errors won't hold much water with Dell support. They'll want you to run their diags. You can download 32 bit diags off of the support.dell.com site and it has a program in it called MPmemory that is similar to memtest, but not quite as sensitive. 

The 32 bit diags program will create a bootable CD you can boot off of to run those tests.

---

### Post by mellowd on 2007-12-04
Could be a heat issue.

---

### Post by woodcarver on 2007-12-04
I would agree with sr20ve, it is most likely a hardware issue. Is your battery covered under the Dell recall? It could be that the positive connections are getting too hot or starting to short.

---

### Post by Skuzniak on 2007-12-04
If you have a Vostro (didn't see a laptop name mentioned anywhere) they are notorious for having ill-fitting batteries, mine included. Usually this is just cosmetic, as in the contacts still connect, but the battery wiggles a little bit. I have heard of it actually affecting the contacts rarely, check the battery contacts to see if they are dusty, dirty or bent out of shape.

---

### Post by inchaos on 2007-12-04
It's an Inspiron 1420n.

I talked to Dell, they did have me run the BIOS diagnostics, that is, F12 -> Diagnostics.

I ran a memtest to 80% and then quit when I finally got in touch with a Dell Linux support guy who could actually speak English and understood what I was saying to him.

The Dell diagnostics included an approximately 30 minute memtest, everything passed. :-\

Are the downloadable diagnostics any different from the ones I just ran?

---

### Post by mellowd on 2007-12-04
I doubt it's your ram, usually if it is your system will crash before it switches off. Becase yours is switching off straight away it makes me believe its a power or heat issue. Modern pc's are designed to automatically switch off before any realy heat damage can take place.

---

### Post by inchaos on 2007-12-04
Trust me, I've been closely monitoring my CPU temps since the first time this happened.

I have yet to see any temps above 45 degrees Celsius.

It's not a heat issue, unless my sensors aren't functioning properly.

My fan works like it always has and I haven't been doing anything processor intensive when this happens.  Just browsing the interwebs.

---

### Post by mellowd on 2007-12-04
Maybe a loose cable somewhere inside then?

---

### Post by inchaos on 2007-12-04
I'm not sure.

I'm going to take out a stick of RAM and see if the it still does this...if it does, I'll swap the RAM in the comp for the RAM that I removed.  At least that way I'll be able to eliminate something as an issue.

---

### Post by sr20ve on 2007-12-05
> **inchaos said:**
> 
Are the downloadable diagnostics any different from the ones I just ran?

No, they're the same.

---

### Post by lisati on 2007-12-05
I might have blinked and missed something in the discussion that ruled them out, but I think someone else mentioned batteries and power supplies....

Many (most?) machines have some kind of on-screen warning if the batteries were getting low and probably something in the log as well, unless there's something happening so quick that the OS doesn't get a chance to warn you.

Having said that, do you normally run of AC? If so, has the power supply suffered some kind of injury? I sometimes trip over the wiring, which possibly contributed to a damaged firewire (and subsequently an unreliable) connection on my video camera.

---

### Post by inchaos on 2007-12-05
This has only happened while on battery power.

My battery has been above 30% each time, there has been no on-screen warning or beep of any kind.

After each power off, my laptop boots and runs normally with battery power, my battery life is not the issue.

I'm still convinced it's a battery or power supply issue.  I don't think it's the RAM but I'm trying to troubleshoot it anyway.  I feel like if it's something major it should be happening more often...not that I want it to happen, but it'd certainly be easier to troubleshoot...not to mention I'd be able to prove to Dell that it's actually happening.

It's pretty unnerving thinking my comp could just die at any second but I have no way to repeat it or test the cause of it.  On the other hand, it might never do it again.  I have no idea.

---

### Post by inchaos on 2007-12-05
Oh, and there's nothing out of the ordinary in the syslog, not before or after the incident.

---

