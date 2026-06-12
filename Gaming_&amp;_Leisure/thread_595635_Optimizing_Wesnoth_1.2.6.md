---
title: "Optimizing Wesnoth 1.2.6"
date: 2007-10-28
forum: Gaming &amp; Leisure
---

### Post by gcrussell1 on 2007-10-28
My apologies if this has been asked before - I ran a search and found nothing relevant in 5 pages of threads (only checked a few that seemed like they might be relevant) - and I'm afraid I've not got the time to look anymore - I still have to plan a grammar lesson to teach in 2 hours...

I started playing Battle for Wesnoth last night on the recommendation of some threads on this forum - I'm running 1.2.6 from the package manager's "wesnoth-all" package on Gutsy. It seems like a great game, but I get a huge FPS drop about once a second, so about half of every second runs at something like 2 FPS, while it runs just dandy the rest of the time.

Hence, the title: I need help figuring out what's causing this FPS drop and how I can fix it. I have also had some trouble with Wesnoth being unsure about whether it should run fullscreen or windowed after any non-Wesnoth process occurs on the screen - it goes back and forth between the two options until I minimize it and open it up again, when it returns to fullscreen mode.

Incidentally, I don't think it's a hardware issue, but I'll post my relevant specs to be sure:

CPU - P4 3.0 GHz Northwood
GPU - 128 MB dedicated Mobility Radeon 9600 with restricted drivers installed - *seems* to be working A-OK
RAM - 768 MB DDR 2700
HD - 5400 RPM, 22 GB partition - 3.5 GB used

Edit: Turned off Compiz effects, problem solved. Should've tried that sooner...

---

### Post by Achetar on 2007-11-01
NOT A HARDWARE ISSUE!!!! Man, how much did u pay for that system? it's pretty sweet!

make sure you have the latest SDL stuff installed (look it up in Synaptic), also, building from source sped it up a heap on my system (wish I had graphics card like urs, 32MB dedicated Video RAM, 96MB shared Video RAM, 768MB RAM, etc.)

Oh, I see you tried turning off compiz, good idea, NEVER RUN A GAME WITH COMPIZ/BERYL RUNNING! saves tons of time

i still recomend building from source, then you get the latest version, which allows more multiplayer and has more units, etc.

---

### Post by gcrussell1 on 2007-11-01
It was about $1200, but I bought it 4 years ago... it's nearing the end of its lifespan with me, but it'll serve some eBayer well once I sell it.

I did upgrade the RAM from 512 to 768, and the HD from 40 Gigs 4200 RPM to 60 Gigs 5400 RPM, which cost about $100, but that's about it.

Thanks for the advice on the SDL packages too, they helped out quite a bit.

---

