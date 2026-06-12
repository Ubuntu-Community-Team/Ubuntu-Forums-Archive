---
title: "Firefox adress bar is broken."
date: 2009-04-11
forum: General Help
---

### Post by emowolf on 2009-04-11
Hey you guys, it seems like my Firefox install went haywire.
I just updated by the Update Manager, tons of stuff got installed as well. Everything works just wonderful, except for Firefox.
When I start it up, my bookmarks are all gone, an untitled page opens instead of Google. I can surf, but they back/forward/refresh/home icons are all greyed out, so I can't use them.
Any reasons as to why this is?

---

### Post by cariboo on 2009-04-11
Is seems like your Firefox profle file got corrupted somehow. your profile is located in ~/.mozilla/firefox, it should look something like this:

```
k7t09bnd.default
```

there will be a random string of letters and nubers before the .default, if you have more than one profile, check the bookmark.html files to see which one is the one you were using.

Once you have saved your bookmarks file delete ~/.mozilla. Firefox will create a new one when you restart it.

Jim

---

### Post by emowolf on 2009-04-11
Okay, I did as you said as deleted the #########.default folder, as I have no other profiles, and now Firefox says it is already running (and tells me to kill the old one) when I click it's icon.
I restart my laptop, I click it, still get the same firefox-is-already-running message. :/

---

