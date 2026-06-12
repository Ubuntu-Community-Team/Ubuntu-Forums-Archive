---
title: "only 3 cores of quad-core &quot;working&quot;"
date: 2007-09-28
forum: Desktop Environments
---

### Post by jasong on 2007-09-28
I have a weird problem on my quad-core computer.

I'm a distributed computing nut, so my computers' cpus are maxed out almost 100% of the time.  The thing is only 3 of the cores on my quad-core go to 100%.  If I have four projects running, generally 2 instances are at 100% and 2 are at 50%.

I've got a theory, based on the fact that the total percentage used when I do top, by which I mean the individual percentages for each program, add up to very slightly more than 300%.  I think there's something going on with Ubuntu that prevents a core, not always the same one from boot to boot, from accepting user programs.  The almost idle core will run stuff, it just doesn't seem to want to run user stuff.  

I'm tempted to try to run my program using the sudo command, but I'm not sure if that would work.  It might just tell me that that's not a necessary command.

I'm using Feisty Fawn 7.04 on an e6600(one of the first quad-cores, not that there are that many choices) with 2Gig of RAM.  Using the Ubuntu OS to get information about the hardware, it looks like there is a ton of information missing, so giving specifics would be a real hassle.  Not that I'm objecting, but I'm going to wait for actual requests before I go digging.  Anything beyond info about the cpu, motherboard or RAM would be a bit of a problem.

Btw, in case I didn't mention it, my computer is a bit of a *******.  It's meant for Distributed Computing and not much else, so it doesn't even have the ability to play sound, other than the error code beeps.

Edit: Running as root doesn't accomplish anything.  Also, I'd like to add that the program I running automatically goes to niceness level 19 when started, so I'm thinking I should look up how to change the niceness level.

---

