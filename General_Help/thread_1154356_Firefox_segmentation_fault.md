---
title: "Firefox segmentation fault"
date: 2009-05-09
forum: General Help
---

### Post by zolistir87 on 2009-05-09
Hello!

Yesterday I installed Ubuntu. Firefox worked fine. Today it won't start, if i try to run it from terminal it gives me a segmentation fault.(I might have installed some firefox update via update manager since then). How can I fix it?(I tried reinstalling,removing it and installing it again, deleting ~/./mozilla)

---

### Post by AndThenWhat on 2009-05-09
Okay, make sure you deleted "~/.mozilla" (without quotes) which is mozilla's/firefox's hidden settings file in your home directory:

```

cd ~
rmdir .mozilla
```

Next, I would recommend completely removing and re-installing anything that says firefox in Synaptic. And then try re-starting because sometimes, for reasons unknown to me, this works even though Linux normally doesn't require restarts.

I suspect that firefox got messed up from an upgrade.

---

### Post by zolistir87 on 2009-05-10
Done what you said(before I posted this), today firefox just started up. Odd. Since when software requires reboot in linux?

---

### Post by AndThenWhat on 2009-05-10
Software doesn't require a reboot in Linux, but sometimes rebooting just works wonders for unknown reasons.

---

### Post by frostedglcok on 2009-06-11
i've found that i had the same problem that started for no reason. first it started with random firefox 3.0.10 segmentation faults and then a few other applications started fouling up. i ran a memtest (from bios on my lanparty dfi mobo) and it turned out that my two oldest ram sticks were bad. 

took them out and kept all good ram sticks in and everything is back to normal. maybe you could run a memtest. it wouldn't hurt.

---

### Post by mgmiller on 2009-06-21
This exact thing just happened to me yesterday.  Segfault in Firefox and Epiphany.  Random crashes or non-starts in pidgin, etc.    

I ran memtest and one of my ram sticks was bad.  Removed it and all is good again.  What a coincidence...

---

### Post by cong06 on 2009-07-14
I keep getting segmentation faults from bookmarks. whenever I right click on one, it crashes. I've already re-built my bookmark library...

---

### Post by zoomy942 on 2009-07-14
any of you with intel hard drive controllers having seg faults?  if so i can help you :)

---

### Post by cong06 on 2009-07-14
> **cong06 said:**
> I keep getting segmentation faults from bookmarks. whenever I right click on one, it crashes. I've already re-built my bookmark library...

I opened my bookmark.html file in firefox, and resaved it.
That seemed to clean up the code in it (there was alot of unclosed <DD> tags in the file)
It lasted for a little, but I think after it synced with xmarks, it got screwed up again. is anyone else having problems with xmakrs and and segmentation faults?

---

### Post by zoomy942 on 2009-07-14
intel controller?

---

