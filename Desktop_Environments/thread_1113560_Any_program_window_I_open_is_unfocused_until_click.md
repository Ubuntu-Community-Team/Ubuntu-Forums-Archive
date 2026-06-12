---
title: "Any program window I open is unfocused until click on it?"
date: 2009-04-01
forum: Desktop Environments
---

### Post by mwillams73 on 2009-04-01
This starting happening yesterday, along with firefox 3 auto zooming(took me three hours to fix that!!) I dont have any programs set to always on top, ive checked the bug fixes none of them worked, to reitterate its not just one program window like some other posters have, its every program window! I dont know whats causing this i uninstalled and completely removed compiz, didnt fix it, I opened every program that ive used in two weeks and checked to see if somehow i accidentally changed the settings, nada. I dont tweak my desktop other than a couple of themes and sum, and of course the desktop cube, but i dont have that any more and before i removed that i checked all the window management settings as other posters had said that it might causing a problem, everything was fine till yesterday, the windows focused when i clicked on the icon just like they are supposed to then out of nowhere they dont focus, this is one program at a time mind you not for example when i have firefox running they appear behind ff's window although that happens also.

So what gives? Im running Hardy on a 1.9 gh AMD athlon 1700+, K7 triton M-board, 1 gig DDR ram,NVidia 6200 LE-A with 256 DDR2 ram, 250 gig Maxtor 7200 rpm HDD

Other than that lil annoying problem everything else is great, even if i cant get it fixed it doesnt really bother me except when im trying to use the terminal and it appears behind FF, or any other program thats focused for that matter. It never did that before and its annoying when im messaging my friends or need to type something because now i have to remember to click on the window before i start typing. Thanx for any help you can provide, If you need any more info let me know, I've been using hardy for awhile now (about 6 months) so im reasonably proficient as long as you give me the proper terminal commands i should be able to provide you with whatever you need so we can figure this out.

---

### Post by mwillams73 on 2009-04-01
Sorry I forgot to mention i checked gconf editor setting for meta city also, no matter what I change or put back to defaults it doesnt seem to help, I also checked the windows menu in system and i dont have "select windows when the mouse moves over them" selected, its just weird. Another thing in firefox after i fixed the zoom going in and out on its own, sometimes the ubuntu forums show up in weird colors, like pink and yellow instead of the tan and cream, although that seemed to fix itself after about an hour or so, but for a lil while i thought someone had dosed me with LSD or something. It doesnt happen in any other webpage i visit so I was wondering if maybe it was just a mod messing around with something? or am i going nuts?

---

### Post by mwillams73 on 2009-04-01
Ok so I figured out how to fix it so the mods can mark this as solved.

I had to reinstall simple compiz, and then went to"system"/"preferences"/"advanced desktop effects settings"/"general settings" clicked on "focus and raise" tab and changed "focus prevention windows" to none,then I set "focus prevention level" to off, then I had to set my "system"/"preferences"/"appearence preferences"/" Visual Effects" to normal and that fixed it. I then had to set the appearences back to no effects cause whenever I watch movies compiz makes them jitter and tear. 

So until next time Mark As Solved!!!!! Yay!!!!!!

Personal note: I love that I was able to fix this for myself, And I hope that anyone else who has this problem is able to follow my directions so that they can have their "focus problems" solved, Also if anyone wants their windows to not steal focus do the opposite of what I did, although I still dont know what caused this problem in the first place but hey I learned something and perhaps was able to help anyone else with their problems too!!

---

### Post by KentonS on 2010-02-26
Wow! Congratulations! How convoluted is that!?!? It reminds me of those "adventure" games - Myst, Zork, and the like - that my wife loves (and I hate).

This issue (among others, of course) has been driving me crazy ever since I upgraded from 7.10 to 8.04.

Thank you!

Kenton S

---

### Post by KentonS on 2010-02-26
Except ... :-(

The solution worked only insofar as it fixed the problem of newly-executed apps being hidden behind a currently-open window.

If all current windows are minimized and I start up a new app using a shortcut key, the new window appears, but doesn't have the focus. I have to click on the window to set focus. The strange thing is that this sounds more like the initial problem description than the one that I fixed by going through MWilliams' steps. The even stranger thing is that if I click on a Panel button to open an app, the app window gets the focus just fine. Go figure!

(You are in a maze of twisty passages, all alike.)

---

