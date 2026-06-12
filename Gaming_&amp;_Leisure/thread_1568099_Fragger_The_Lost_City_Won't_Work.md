---
title: "Fragger The Lost City Won't Work"
date: 2010-09-04
forum: Gaming &amp; Leisure
---

### Post by belkinsa on 2010-09-04
So Miniclip releases a new game called Fragger The Lost City.  I go to play it on their site.  It loads, but when I click "Play", it goes to an ad about Fragger for the iPhone.  But when I click the green bar on the ad, it doesn't let me to play.  I try to click back and then Firefox crashes on me.  After a minute of waiting, because Firefox says it needs to close, I reopen it.  It takes my back to the page, but lucky I can close it without Firefox crashing.  But one other thing happens, my theme goes to what the attached screen shot shows.  Lucky, I can fix that with a reboot.

Is anyone having the same problem with that game?  (Windows and Mac counts this time)

---

### Post by lovinglinux on 2010-09-07
Yes, I have experienced the same problem with Firefox 4.0b5 and Ubuntu Maverick 10.10 32bit, but only once. If that happens again, kill plugin-container. It should allow you to go back working with Firefox.

```
killall plugin-container
```

Now it takes some time to show the game after the ad, but it works.

I'm running Firefox 4.0b5 and Ubuntu Maverick 10.10 Beta.

---

