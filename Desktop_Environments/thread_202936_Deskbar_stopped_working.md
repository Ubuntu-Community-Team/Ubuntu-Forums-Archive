---
title: "Deskbar stopped working"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Carandol on 2006-06-24
I wonder if anyone else is having this problem. Deskbar was working fine (with beagle) until yesterday. Now, when I boot up, Deskbar doesn't appear, none of the other icons to the right of it on the panel appear either, and none of the buttons on either panel work. If I kill the deskbar, the rest of the icons load, and everything starts working.

---

### Post by momaw27 on 2006-06-24
I'm having the same thing happen to me... anybody know what's up?

---

### Post by s_p_a_r_k_y on 2006-06-29
its happening to me as well, I had to unload it. You can kill it from the command line with 
```
pkill -9 deskbar
```
and it will ask you to unload it or reload it. For a while I could then reload it, but now it has just crapped out and doesn't load at all. I deleted the folder in .gnome2/ for deskbar in hope that it was just a bad conf, but that didn't do the trick. Perhaps I'll delete its gconf entry and hope that gets rebuilt. I'll let you guys know.

---

### Post by s_p_a_r_k_y on 2006-06-29
OK I went into gconf-editor did a search for deskbar, then went to the first hit for it, "app/deskbar/" or so. I then just deleted a few entries out of the "enabled_handlers"
I just did all the mozilla ones and then it loaded. I haven't logged out or anything yet. Give it a try, hope it works for you guys :)

---

### Post by IbeeX on 2006-06-30
Same thing is happening to me. :confused:

---

### Post by LifeIsAFractal on 2006-07-31
quick thought.  I have the same problem and I have an Nvidia 6800go.  My girlfriend is running an almost identical install of Ubuntu that I maintain and she has an ATI and her desk bar is working flawless.  The only other major difference is that I have the begal plugin for deskbar and she doesn't.  Maybe we can narrow down what setup is causing this problem cuz I love that deskbar and want it back. ~cheers~

---

### Post by LifeIsAFractal on 2006-07-31
well I looked a little more and if you remove all the beagle handlers in /usr/lib/deskbar-applet/handlers then it will work... minus beagle :-(.  As I said in my last post my girlfriend didn't have beagle on her computer so I think there is some kind of a conflict with deskbar and beagle right now.  Hope the devs iron this out soon. ~cheers~

---

### Post by ape on 2006-07-31
I was having this same issue and also noticed that the beagle handlers were causing the problems.  I remove my .beagle directory and restarted the deskbar and haven't had the problems since.  Of course this means that beagle is having to re-index everything...

---

