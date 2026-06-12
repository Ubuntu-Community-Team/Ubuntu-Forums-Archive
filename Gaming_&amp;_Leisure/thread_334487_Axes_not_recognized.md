---
title: "Axes not recognized"
date: 2007-01-09
forum: Gaming &amp; Leisure
---

### Post by pjkoczan on 2007-01-09
When trying out my controller (logitech rumblepad 2) in any program that supports joysticks (for me, this is mostly emulators, supertux, tux racer, and the rare other thing), the buttons work fine, but the axes don't.

For instance:

pete@pete-home ~ $ zsnes

(... random crap)

Device 0 Logitech Logitech RumblePad 2 USB
  6 axis, 12 buttons, 0 hats, 0 balls

And I can't configure zsnes to use the axes (they work fine in jscalibrator, even though two axes should probably be seen as hats by zsnes, as they are configured to be hats in jscalibrator).

I've seen this problem pop up a lot before and I haven't found anything remotely close to a solution for it. Any help? I'm using packaged versions (.deb's) of just about everything.

PDK

Note: This happens in snes9x (which I don't think has axis support in linux that I've found), fceu, mame, and just about everything else. I just used zsnes as a convenient example.

---

### Post by Cirrocco on 2007-01-09
Super Nintendos didn't have analog axis controllers, though.  they weren't supported until N64.

---

### Post by pjkoczan on 2007-01-11
> **Cirrocco said:**
> Super Nintendos didn't have analog axis controllers, though.  they weren't supported until N64.

Quite true, but this controller also has a 2-axis digital pad, and the games don't recognize when I press up or down on it, and it probably should, since all the other buttons are recognized. I fear that the hats aren't being recognized, even though I set the d-pad to be a hat.

My question (or questions, I guess), to those who were paying a little more attention and not veering off topic, is this:

Is this fixable? Is there a way to (reliably and relatively cleanly) hack either the games, emulators, or controller calibration to get this to work?

Failing that, is there a controller on the market that does reliably work under these situations? I mean, I like that controller, but it's only a controller.

So, any ideas?

I'm using edgy i386, jscalibrator, drivers, and all games are currently installed via .deb packages.

---

### Post by DoktorSeven on 2007-01-11
I had a similar problem that was fixed by removing the **analog** module:

**sudo rmmod analog**

It was a digital-only pad, but didn't negatively affect my other controller (Playstation controller->USB in analog mode).

(adding the line **blacklist analog** to /etc/modprobe.d/blacklist makes that permanent)

---

### Post by pjkoczan on 2007-01-12
> **DoktorSeven said:**
> I had a similar problem that was fixed by removing the **analog** module:

**sudo rmmod analog**

It was a digital-only pad, but didn't negatively affect my other controller (Playstation controller->USB in analog mode).

(adding the line **blacklist analog** to /etc/modprobe.d/blacklist makes that permanent)

Didn't work, but thanks anyway.

---

### Post by pjkoczan on 2007-01-18
Anyone?

---

### Post by pjkoczan on 2007-03-19
The solution, as I've found, is to use the newest version (1.51, i believe). A .deb package can be found with a little searching.

---

