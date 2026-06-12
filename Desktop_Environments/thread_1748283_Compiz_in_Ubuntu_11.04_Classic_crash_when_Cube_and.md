---
title: "Compiz in Ubuntu 11.04 Classic crash when Cube and Expo are together"
date: 2011-05-03
forum: Desktop Environments
---

### Post by Eversmann on 2011-05-03
Hello.

For starting a new thread with this exact issue, i'm having a weird problem with Gnome Classic and Compiz:

In CCSM, when expo and cube are enabled (for instance, expo is enabled and you click on the cube) ccsm crash, and all the plugins change to disabled (so everything quit).

If i do the opposite, cube enabled (and working) and then click on Expo, everything crash the same way.

is anyone having the same problem?

---

### Post by Tangerine Tom on 2011-05-18
> **Eversmann said:**
> In CCSM, when expo and cube are enabled (for instance, expo is enabled and you click on the cube) ccsm crash, and all the plugins change to disabled (so everything quit).
 
Yeah I've had a similar problem, only mine COMPLETELY crashed.  When I came out none of the GUI was working properly.  Unity had gone, date/time/settings had gone, it was still gone on a restart.  I'm going to do a repair reinstall and see if that fixes it.  Strikes me as a little unstable tbh...

---

### Post by Blasphemist on 2011-05-18
This doesn't affect all of us so I think you'll find another setting that you both have is causing this. I'm thinking number of workspaces is where to start looking. That is referenced in this thread. Ensure that it is 1x4.
[http://ubuntuforums.org/showthread.php?t=834401](http://ubuntuforums.org/showthread.php?t=834401)
What version of ubuntu are you using?

---

### Post by usernumber12 on 2011-09-10
I had the same thing happen to me earlier today. I tried running "unity --reset" in a terminal several time with no success. I ended up removing Unity,and re-installing it. Now I'm back to normal.

---

### Post by Blasphemist on 2011-09-11
This post is great on how to set up the cube in natty. At the end it also gives the best and complete reset procedures should you stray to far. [http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Thanks to forum user wildmanne39 for this great post.

---

