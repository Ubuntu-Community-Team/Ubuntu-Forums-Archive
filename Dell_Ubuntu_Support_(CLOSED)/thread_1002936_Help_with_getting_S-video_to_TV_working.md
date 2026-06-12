---
title: "Help with getting S-video to TV working"
date: 2008-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chee on 2008-12-05
hi
i have been running Ubuntu on my Dell Inspiron 6400 for a couple years now and really like it.  my only problem is that i have to revert back to my windows partition to use the S-video to my tv.  i have tried some things in the past all of which failed.  i wish i could remember what i tried to be more help but i can't.  any help would be greatly appreciated.

thank you 
Wes

---

### Post by chee on 2008-12-08
so if no one has an answer (the more reading i do the more i start to think there is no fix for me) do i have any other options?  basicly i would like to watch somethings that are on my computer but aren't really worth burning to a DVD.  if windows can do then there should be a way!!  ha! just kidding i know its more complicated then that especially with all the different computer brands out there.  

any help would be great thank you :confused:

---

### Post by moore.bryan on 2008-12-08
i ran into the same problem with my lenovo z61e and discovered through months of searching, there is no solution for me; perhaps--and unfortunately--you fall into the same boat.

have you already tried all the different xrandr tricks?

---

### Post by chee on 2008-12-08
please explain as i have no idea what those are.  i am a super noob also so please explain appropriately.  i can get by as i have been running linux for 2 years but a good friend set it up for me,  now i just maintain :p

thanks
Wes

---

### Post by moore.bryan on 2008-12-08
no worries... xrandr is simply a front-end to [randr]("http://en.wikipedia.org/wiki/Xrandr"), which is a way to dynamically change video-out options. one of the main "problems" with linux and s-video out seems to be the on-the-fly screen resolution change which windows automates, but which linux must be done manually. for example, your television is probably only capable of 800x640 at a certain depth, but your default outputs are probably much wider and/or deeper than that. or, at least that's how it was explained to me.

---

### Post by chee on 2008-12-08
so is there maybe the potential that my s-video does work but i simply need to resize before using it as the TV doesn't have the capability of showing the image?  cuz that would be sweet.

---

### Post by moore.bryan on 2008-12-08
there's a good chance that's you're problem. go to synaptic (system>administration>synaptic) and install grandr, the graphical front-end for randr. see if that fixes your issue.

---

### Post by chee on 2008-12-08
i will definitely try that tonight,  i am at work right now or i would try it right away.  i will keep things posted here.  thanks for the info i do appreciate it.

---

### Post by lahook on 2008-12-09
I'm not sure what video card you have. On my XPS 1530 I had to install the Nvidia proprietary drivers.

---

### Post by chee on 2008-12-09
i didn't get a video card when i bought it so it would be whatever the integrated one is (and i can't remember which one it is).  if i was at home i would check it out.

---

### Post by moore.bryan on 2008-12-09
your on-board video *might* still be nvidia, but i wouldn't think so. let us know if the randr method works for you...

---

### Post by chee on 2008-12-13
sorry guys i would try this out but my TV died on me.  i would be disappointed but it was the old tube style and i got the extended warranty so i get all my money back towards a new LG LCD.  its on the way.  i will try it pronto when that happens.  thanks again

---

### Post by moore.bryan on 2008-12-14
wow... when it rains it pours. at least it sounds as if your replacement is an upgrade; keep us informed, will you?

---

