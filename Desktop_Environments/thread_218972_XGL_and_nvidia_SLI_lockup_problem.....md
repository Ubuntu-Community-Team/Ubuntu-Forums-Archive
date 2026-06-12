---
title: "XGL and nvidia SLI lockup problem...."
date: 2006-07-19
forum: Desktop Environments
---

### Post by Flecko on 2006-07-19
Hello all,

First, a little background to my problem. I've had XGL/compiz working on my dapper computer for awhile(and have been using the quinn debs for a month or so) with no problems whatsoever. I use the official drivers in dapper for my Geforce 6600GT and have had no stability problems whatsoever.

However, my computer has a second 6600GT in it as well in SLI configuration. I've never really used them together(it was an impulse buy when they were on sale) but seeing as the nvidia linux drivers now offer SLI support, I figured what the hell. I set up my xorg.conf (using nvidia-xconfig --sli=AFR and I've also tried AUTO and SFR.) Now, X launches and works fine with no lockups, but the lockups occur later.

I use a script called Xgames to launch things like Cedega or any game that requires fullscreen direct rendering in a seperate X session. This works fine with XGL and one nvidia card, but when I have SLI enabled, this causes the screen to garble when switching screens and causes a hard lock. No mouse response, no keyboard response, no nothing.

I can also reproduce this without using the Xgames script. If I switch screens using CTRL+ALT+F(1-X) it produces the same garbled screen and hard lock.

My question is, has anyone else here run into lockups with XGL and SLI on a nvidia card? If so, any remedies or recommendations?

For now, I just use one card...but it feels like I'm not really using the whole potential of my setup. Especially now that Oblivion is playable in Cedega.

Thanks gang!
-Flecko

---

### Post by fain on 2007-05-23
Yes I have :( I enabled AFR and Auto and AFR crash is immediate as soon as i bring up glxgears or any other 3d app. When in Auto, I played nexuiz for about 15 min just fine, glx  gears works great too. Then i brought SWG in wine and BOOM!!!! by by ubuntu. Every thing worked great while not in sli mode. I figured it might've been something in wine. I left my computer up over night with a random screensaver and it was dead in the morning on a gl screensaver.

          some times my mouse daemon is responsive in these crashes and sometimes its not. but what is sure nothing else i try will work. all windows and gadgets are locked up. i cant even ctrl alt f1 in to a term. i have to hard reset :( 
         
          I've had sli working in ubuntu edgy and suse 10.1 i think. i know it was working in edgy but i was using the drivers from nvidia's website. i might try that soon. Are the drivers from the site the same as the ones from the repo?

          One more question. whats the difference between multigpu and sli option in nvidia-xconfig?

---

