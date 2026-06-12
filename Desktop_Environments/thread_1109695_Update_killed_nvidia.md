---
title: "Update killed nvidia"
date: 2009-03-29
forum: Desktop Environments
---

### Post by Sin@Sin-Sacrifice on 2009-03-29
I think some things have changed around here because I dont see "Mark as SOLVED" in the thread tools but this has been solved.

I saw an update for the headers for 2.6.24-24-rc and figured i might as well get'er done after 3 days of postponement and go figure.... it killed the nvidia drivers, Running an on-board 6150 nforce 430 chipset on an m2n board (stock m8000n box...filthy HPs) and hardy studio. I assume the nforce 430 are my realtek hardware because I now have no sound too. I tried reconfiguring xorg.conf... Are there any drivers out there that might work better with this configuration? Or am I just being a dumb stoner and not seeing something here? Also... probably another dumb stoner mistake but I also get "sudo: unable to resolve host Purgatory" after just about every command using sudo on this thing. I dont remember changing anything having to do with a host name... my computer name is purgatory but isnt that "localhost"??!! Weird... I probably messed with something and ****** that up but I'm not sure how to get rid of that. Any ideas?

---

### Post by edweird13 on 2009-03-29
I think it has more to do with the updates to X than it is the drivers.

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
Well I assumed as much but do I have to revert or get drivers better suited for my kernel or configure x differently or just grow a few braincells back? I think I'm just being an idiot and not seeing a simple solution but for all I know it could be support issues.

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
Little bitty bump for day 2. Hoping someone out there has an idea.

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
Well... I got the graphics drivers working but the sound is still off. All I did was what I should have checked on in the first place.... which was go into synaptic and make sure the correct modules were installed. Ugh... go figure. Anyway... off to find out the sound problem.

---

