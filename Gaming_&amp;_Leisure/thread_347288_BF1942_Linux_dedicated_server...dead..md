---
title: "BF1942 Linux dedicated server...dead."
date: 2007-01-27
forum: Gaming &amp; Leisure
---

### Post by Silverfox on 2007-01-27
Hi all.

Running 6.06lts server. Pretty much the default LAMP install of the AMD-64 version. Had some trouble initially with missing 32 bit compatibility libs, fixed, and had the server running flawlessly for about 2 months. Today, my weekly chores of "apt-get update" and "apt-get install" appears to have broken the server. I'm unable to get it to start, it dies with the following error:

```

silver@RDES-Gamers:~/bf1942$ ./start.sh
./start.sh: using statically linked binary
Fatal error: Failed to bind socket

silver@RDES-Gamers:~/bf1942$

```

I neglected to take note exactly of what security update occured, and I'm too noobish to know where to look in my logs for that info. I remember is being largish (30mb?) and consisting of 3 or 4 libc packages (sorry, I was in a hurry, and distracted :( ) and I think the version was 2.6.2

The only thing that's changed were the security updates. Any ideas on how I can fix this? Oh, btw, using the latest released version of the bf1942 linux server (it's an old game, but we still have a blast playing it). I'd be happy to give you more information if you could direct me to where I should look. :confused: 

Thanks

---

### Post by Silverfox on 2007-01-27
ps I found the log I was looking for (dpkg.log). The files upgraded were:

2007-01-26 17:09:10 upgrade libc6-i386 2.3.6-0ubuntu20 2.3.6-0ubuntu20.2
2007-01-26 17:09:11 upgrade libc6-dev 2.3.6-0ubuntu20 2.3.6-0ubuntu20.2
2007-01-26 17:09:12 upgrade locales 2.3.18 2.3.18.1
2007-01-26 17:09:13 upgrade libc6 2.3.6-0ubuntu20 2.3.6-0ubuntu20.2

Is there a way to undo these? As I stated, I'm a linux noob, I possibly should have posted this in the Absolute Beginners area? 

(but I did learn something, where to find my upgrade logs! :) )

---

### Post by Silverfox on 2007-01-27
NM. A couple of restarts and my problem seems to have vanished into the ether. I had restarted the system after the upgrade, but I just restarted it now out of frustration and the game server now appears to be working again.

Move along, nothing to see here.....:D :)

---

### Post by tocleora on 2007-01-27
It's weird to see this post, the game came out what, 2001? 2002? And yet my coworkers just introduced me to the game last week. I went out and bought it first of last week and I've played it pretty much daily since. :) I'm apparently very noob at it and one of my coworkers said I was griped out during the game yesterday (didn't even notice myself) but hopefully I'll learn. ;)  Is your server public?

---

