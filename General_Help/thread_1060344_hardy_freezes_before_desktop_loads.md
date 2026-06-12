---
title: "hardy freezes before desktop loads"
date: 2009-02-04
forum: General Help
---

### Post by daweefolk on 2009-02-04
my ubuntu hardy heron worked fine for the longest time then today for no apparent reason it froze up when i tried starting up. what happens is when the desktop is in the process of loading (cursor appears, background is loading) it freezes.
it either freezes before the background even loads, after the background loads but nothing else, background and taskbar/launcher panel load (but are unclickable), or everything loads... but when everything (desktop icons, launcher and taskbar, background, etc) loads, half the icons are missing from my launcher and nothing responds when i click on them. also, when i bring up the terminal with they keyboard command, i can't input anything at all. what's going on? and how can i fix it?

---

### Post by utnubuuser on 2009-02-04
Hi -- have you tried getting to your terminal through recovery at boot?

And if you can,  maybe try:> sudo dpkg --configure -a to see if it'll straighten out what's amiss.

---

### Post by daweefolk on 2009-02-04
i tried sudo dpkg --configure -a and started it up... but nothing.
i DID however notice something i didn't before. my computer's a little noisy, and down by my mousepad's a little light that usually shows when my computer's working. when i tried starting up, the desktop background loaded and then my computer just stopped. i heard absolute silence and that light was off. it's almost like my computer just kinda shut off at that point.

---

### Post by daweefolk on 2009-02-04
um..... ok... i fixed it. for some reason, having the system sounds turned on did it. i was able to start up in an older kernel version, turned system sounds off, (after remembering that's the ONLY thing i did "odd" before it happened) and voila! my computer works again.

---

### Post by utnubuuser on 2009-02-06
great!  Is this a bug, and have you reported it?

---

