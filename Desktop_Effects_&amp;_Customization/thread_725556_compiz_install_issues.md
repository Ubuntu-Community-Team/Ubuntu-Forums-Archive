---
title: "compiz install issues"
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by setotitan on 2008-03-15
hey guys this is my inaugural post here so be gentle ;) i've used windows my who life, dabbled a little in OS X for work, but never used linux. a buddy of mine gave me a ubuntu disc months ago and i never gave it a second thought. pardon my superficialness but i've alway though linux was to ugly an OS to use. i'm drawn to the sleekness of other OS'. however just the other day i was cruising around and i saw a demo of a machine running Beryl. i cannot lie i was truly fascinated.  not ready to part with my windows ways i did some research and found you can dual boot ubuntu so you can have both OS'. long story short i'm giving ubuntu a test run, i've got the Gutsy version 7.10. and much to my dismay i've learned Beryl cannot be run from Gutsy, that the last version that could handle it was Feisty :( 

however from what i've been told, Beryl was just a side shoot of Compiz and that it's merged back into Compiz. even better that 7.10 comes with Compiz (kinda). so yearing for some sort of eye candy i'm attempting to make it work however i can't seem to make it happen.

i went to Appearance and checked Extra on my Visualization tabs. I then when through a wizard and loaded NVIDIA card, it's in the Restricted Drivers list but it has a check next to Enabled and under Status it says in use. i then when to Add/Remove and installed CompizConfig Settings Manager. then i rebooted my computer. i now see CompizConfig Settings Manager listed under Preferences however every time i click it nothing happens. i go to Appearances and under the Visualization tab I see Custom, it lets me check Custom but when I click th preferences button next to it nothing happens. and when i close the Appearences tab and reopen it Custom is unchecked and it's back to Extra.

my question is 2 fold 

A) is Compiz on Gutsy not even near as cool as Beryl on Fiesty and should i screw trying to make Compiz work and just install Fiesty?  

OR

B) if Compiz is my best option what do i need to do? i know sometimes i see if you type something in the Terminal it give you some diagnostic to help, if someone tells me what to type i can post the results. thanks so much for any help!

---

### Post by satanic-yobbo on 2008-03-16
compiz is definateley worth the trouble for sure and is way better than beryl i would just try uninstalling and re-installing ccsm  and see what that does for you.
 its a whole lot of fun when it gets going

---

### Post by Ub1476 on 2008-03-16
```
compiz
```

Write that into the terminal to get troubleshooting output.

---

### Post by Zorael on 2008-03-16
Are you sure only 'compiz' is needed and not 'compiz --replace'? Maybe it's changed and I'm just slow to realize.

Anyway, Beryl is old, go Compiz. :>

---

### Post by FuturePilot on 2008-03-16
> **Zorael said:**
> Are you sure only 'compiz' is needed and not 'compiz --replace'? Maybe it's changed and I'm just slow to realize.

Anyway, Beryl is old, go Compiz. :>

Yes it used to be "compiz --replace" but in 7.10 they have added a Compiz wrapper script for starting Compiz. Now you only need "compiz"

---

### Post by setotitan on 2008-03-16
i figured it out, thanks! turns out another post had the answer. i X'd it out so i don't know what it technically was, but i didn't want people trying to still help me when it was resolved. however i'm so glad to see how supportive the ubuntu community was ;)

---

