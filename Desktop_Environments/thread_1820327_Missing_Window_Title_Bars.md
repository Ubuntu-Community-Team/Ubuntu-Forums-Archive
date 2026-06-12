---
title: "Missing Window Title Bars"
date: 2011-08-07
forum: Desktop Environments
---

### Post by BSOD64 on 2011-08-07
I'm using gnome in Ubuntu 11.04 x64.  When I was poking around in the CompizConfig Settings Manager all my window title bars disappeared. I found I could type "metacity --replace" in to the terminal and that would kinda fix the problem (I've got no effects at all) so I put the command in StartupApps. My desktop is now usable but I'd like a real fix.  Thanks

---

### Post by clegends on 2011-08-07
Hi, you probably changed the wrong setting in 'Windows Decoration' under effects. Go back into CCSM, open 'Windows Decoration', and check the 'command' entry. Here you can do two things. If it metacity is working for you, then type
```
 metacity --replace
```
in that box. Personally, I preferred emerald for my windows manager in 10.10.

At the moment I'm using Natty (working brilliantly mind you... and loving Unity), and my command in that box is:
```
/usr/bin/compiz-decorator
```

Not sure if that will work in 10.10 however but you can try it. Natty is great, and I recommend it. Cheers.

---

### Post by BSOD64 on 2011-08-07
I took 'metacity --replace' out of startup and tried both those commands but I still have minimal window effects.

btw Like I said before I am using Natty, but not Unity.

---

### Post by BSOD64 on 2011-08-09
bump

---

### Post by Luke M on 2011-08-10
Enable "effects" -> "window decoration" in compiz settings.

---

### Post by BSOD64 on 2011-08-12
Thanks, it worked.

The reason I thought it was still broken is that I had a bunch of other CCSM settings turned off. When I turned them back on everything was back to normal.

Thanks so much :)

---

