---
title: "Very laggy Steam / CS-CZ"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by CheeseEatingBulldog on 2007-07-22
I have finally gotten steam to install again, and work for that matter. Counterstrike CZ installed fine and launched successfully. BUT, (and I noticed this last time it did work) gameplay is incredibly laggy (nothing else running at the time). It bottlenecks every 3 seconds or so, I just don't get how, seeing as I have a 7MB Down / 1MB up line. Do I have to open a port on my router? 

This is both the case in fullscreen and in box on desktop.

---

### Post by CheeseEatingBulldog on 2007-07-23
So nobody who uses wine / cedega here has any problems with choppy gameplay? Nobody?

I am running WINE 0.9.41, and have tried to tweak the game but it appears to be wine itself that is bottlenecking. I turned down the graphics, disabled the mic and direct hardware sound, reduced smoke quality and reset rates, cmd_rates and update rates. Ensured there are no other sound deamons running and enabled OSS in winecfg. I just don't understand why the game is so choppy, it runs smooth inbetween 3-6 seconds interrupts of lag. (when looking at the system monitor, it indeed shows mountains of lag every so long, like sharp jagged mountains. What is blocking?

---

### Post by willskills on 2007-07-23
Do you have drivers installed for your graphics card? By the looks of things you're going to need to grab the Legacy Nvidia drivers, if you are using something like a GeForce2...

I play CS Source at about ~50 -75fps with smoke & 30 ppl on the server, and that is running on Ubunutu......

If it's Ifrit you're using - you don't say how much RAM you have...... infact you've given us very little information.

n.b. - there are so many posts on this topic, many people did not reply, probably, because there is so much info on the subject readily available, all you need to do is the use the [Search Button](http://ubuntuforums.org/search.php)

---

### Post by CheeseEatingBulldog on 2007-07-23
Well thanks for taking the time to reply, but I certainly don't need the legacy drivers (my geforce2 64 mb mmx 400 is listed in the normal glx driver).  As for ram I have a gig of DDR, so that should definitely not be a problem for a 10 year old game.

One thing I can think of is maybe making a separate login without AIGLX (if that is even possible). But it seems to be a wine problem, that can't handle continual traffic.

---

