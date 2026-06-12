---
title: "Battlefield 1942 Quest: Need Help!"
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by jack_teagarden on 2007-04-28
I need help with wine + BF1942. I know Cedega would probably work better, but I have no cash!
My box is a 7.04 feisty w/ 0.9.36 Wine, on a 2.66 Celeron D with a Nvidia GeForce 6200

Okay, the problem:
I patched it to 1.6 and added a no cd crack because it was complaining about a few DLL's,
and now it runs. I deleted the .bik videos because they froze up (right after starting) and now I can get to the menu, but it runs *super* slow and freezes up.

Any ideas, anyone?
Anything helps, I really want this to work!!

---

### Post by jack_teagarden on 2007-04-28
Anything?

---

### Post by bastiegast on 2007-04-29
Try running it with```
 export WINEDEBUG="fixme-all" && wine BF1942.exe
```

Also, I looked it up in wine appdb and it has bronze rating so I am not sure if its even playable in wine.

---

### Post by TheTank on 2007-04-30
add the command line option restart=1 (IIRC) and it will skip the intro films.

also the main menu, by default, has a film running in the background, but on a win system there are no problems if you delete the films.

It should work on wine as there are others in this forum that play it as well

---

