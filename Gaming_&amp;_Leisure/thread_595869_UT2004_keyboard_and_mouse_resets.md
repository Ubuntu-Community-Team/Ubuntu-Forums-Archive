---
title: "UT2004 keyboard and mouse resets"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by ToastyX on 2007-10-29
Sometimes, maybe every 10-20 minutes or so, my keyboard and mouse would seem to reset while playing UT2004. All of a sudden, I'd be facing down, and whatever key I was holding stops registering until I let go and press it again.

Anyone have any idea why this is happening?

---

### Post by Crafty Kisses on 2007-10-29
> **ToastyX said:**
> Sometimes, maybe every 10-20 minutes or so, my keyboard and mouse would seem to reset while playing UT2004. All of a sudden, I'd be facing down, and whatever key I was holding stops registering until I let go and press it again.

Anyone have any idea why this is happening?
Are any resources being used?

---

### Post by Cappy on 2007-10-30
There was a thread about it but I don't know a solution.
[http://ubuntuforums.org/showthread.php?t=557543](http://ubuntuforums.org/showthread.php?t=557543)
I haven't had it happen since I upgraded to Gutsy either.

---

### Post by ToastyX on 2007-11-01
> **Codename said:**
> Are any resources being used?
I don't think it's a resource problem. Nothing is hogging the CPU or RAM. UT2004 runs very smoothly.

> **Cappy said:**
> There was a thread about it but I don't know a solution.
[http://ubuntuforums.org/showthread.php?t=557543](http://ubuntuforums.org/showthread.php?t=557543)
I haven't had it happen since I upgraded to Gutsy either.
I'm using Gutsy. I've been using Linux for a long time and haven't ever encountered this problem until installing Ubuntu, so I'm stumped.

---

### Post by ToastyX on 2007-11-05
I finally figured out what's causing the problem. It's gnome-screensaver. For some reason, it tries to activate while I'm playing, and when it does, it eats my input. I verified this by setting the screensaver to activate after one minute. What's weird is I don't actually see it activate. It just eats my input. It seems to be related to this bug: 
[https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/32457](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/32457)

I ended up creating a script to kill gnome-screensaver before starting ut2004, and the problem stopped happening. What I don't get is why more people haven't reported this problem. Considering gnome-screensaver is enabled by default, it should be a common problem, but I'm having a hard time finding other people who have encountered this problem.

---

