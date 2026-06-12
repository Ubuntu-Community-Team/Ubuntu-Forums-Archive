---
title: "overclocking cpu"
date: 2009-05-12
forum: General Help
---

### Post by shadow120 on 2009-05-12
i'm thinking of overclocking my cpu and was wondering hiw i would do this and how much i can safely overclock my specs are

dell dimension 2400
ubuntu 8.04
kernel 2.6.24-24 generic
intel pentium 4 2.40GHz
2gb ram

thanks for the info

---

### Post by cybrsaylr on 2009-05-12
Why?
Thought about doing it in the past till reading it will shorten the lifetime of your PC and if not done right burn it out.

---

### Post by Sewje on 2009-05-12
You'd need to look in your BIOS, but usually premade computers usually prevent overclocking as standard so they can charge extra when they enable it as and option...

Old computers don't really benifit much from overclocking anyway.

---

### Post by shadow120 on 2009-05-12
no real reason just trying to get as much as i can out of it.  not really worried about shortening the life of the cpu as long as i dont fry it right now.  what do i need to look at in the bios

---

### Post by Skripka on 2009-05-12
> **shadow120 said:**
> no real reason just trying to get as much as i can out of it.  not really worried about shortening the life of the cpu as long as i dont fry it right now.  what do i need to look at in the bios

It depends on exactly what CPU you have, and how good a BIOS you have.  2.4 gHz Pentium4s came in 3 major varieties off the top of my head.  Which of these you have will tell you more about what can be done.

Odds are, your bottleneck is NOT at your CPU, unless you are doing lots of multitasking.  Your CPU is about 7 years old, and is using memory 7 years slower than current speeds--your memory is probably on DDR, and probably only running somewhere between 400-533mHz versus data rates 3 times faster at the current highest speeds.

Sure you can try to OC the CPU, but odds are it won't get you much.

You'll need to look in the BIOS to see what options you have to control....Odds are, about all you can tweak up would be RAM voltage, and FSB speed.  Odds are...this isn't much to work with, and with an inadequate PSU, you won't get stability.


Overclocking is an art, more than a science.  _***[COLOR="Red"]If you push things to hard, or in the wrong manner, you'll render your machine unbootable until you reset the BIOS jumper on your mainboard.[/COLOR]***_

If I am confusing you with terms here, it means you need to learn more about what you are proposing to do, before you go messing with things.  Overclocking can work well, or it can cause your machine to no longer boot, or anywhere in between.

The machine I run (in my sig), has the CPU overclocked ~30% (stock is 2.8 3-core), and I managed to activate a 4th core on it (the CPU in this box is only sold as a 3-core, but there is a 4th on it)-due to BIOS fiddling.  And it works.  But then again, I had to know a great deal to get it that way.

---

### Post by shadow120 on 2009-05-12
Skripka - cpu is intel pentium 4 2.40GHz level 2 cache: 512 kb integrated memory is 2x 1GB kingston kvr 333/1gr 2.5v if that helps thanks for all the info

---

### Post by Skripka on 2009-05-12
> **shadow120 said:**
> Skripka - cpu is intel pentium 4 2.40GHz level 2 cache: 512 kb integrated memory is 2x 1GB kingston kvr 333/1gr 2.5v if that helps thanks for all the info

Yep.  Your problem most likely is the very slow RAM speed....overclocking the CPU won't do much.

Understand that your CPU has 1 core.  _That 1 core of your CPU, is faster in terms of clock speed than 1 core from ANY current generation multi-core CPU_.  Overclocking it won't do much at all.  

You can try tweaking/overclocking your RAM -but even that won't give you much noticeable improvement, your machine would still be left in the dust by even the lowest end of current generation desktops.

---

