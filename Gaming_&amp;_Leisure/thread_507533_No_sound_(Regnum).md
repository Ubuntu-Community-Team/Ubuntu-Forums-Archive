---
title: "No sound (Regnum)"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by Bofur on 2007-07-23
I just downloaded Regnum Online and am getting no sound. Other games that run under wine like warcraft 3 and steam work fine soundwise but Regnum wont. Does anyone have any ideas? Thanks.

---

### Post by cogadh on 2007-07-23
Are you running Regnum under Wine? You shouldn't, it has a Linux native client, you should just install that instead.

---

### Post by Bofur on 2007-07-23
No I'm running it natively.

---

### Post by cogadh on 2007-07-23
Okay... then why mention Wine games with working sound?:confused: Nevermind, it's not important.

Do you have the libalut0 package installed? I believe it is required for the sound to work correctly. Also, have you tried launching the game from the terminal to see if there is any terminal output that might indicate what the problem is?

---

### Post by Bofur on 2007-07-23
I installed that package and now the sound works! But, there is a problem, its choppy as hell and I don't know why. Any ideas?

---

### Post by cogadh on 2007-07-23
Is it the sound that is choppy or is the game itself? I've always found Regnum to be a little bit laggy, no matter what I do.

---

### Post by Bofur on 2007-07-23
Just the sound, the game runs fine.

---

### Post by hikaricore on 2007-07-24
Run this:

```

gedit ~/.openalrc
```

Paste This:

> (define devices '(native))

Save the file and try running the game again.  ^_^

---

### Post by gabox on 2007-08-14
:popcorn: im going to do a party....this works really fine

MY POOR PC: AMD ATLHON XP@1100 Mhz MSI KT4A ULTRA +MSI NVIDIA 5700LE 256DDR+Kingstone 754MB DDR400......and my sound is an C-MEDIA 8738MX:popcorn:

THANKS A LOT...cya next time

---

### Post by DouglasAWh on 2007-11-07
But what if the problem was in WINE, what would you do then?  I found [http://osdir.com/ml/emulators.wine.user/2004-03/msg00272.html](http://osdir.com/ml/emulators.wine.user/2004-03/msg00272.html), but it's from 2004.  I also found a link from 2006, but I'd like something Gutsy specific, if it exists.

---

### Post by cogadh on 2007-11-07
What in the world does that have to do with the thread topic? You really shouldn't hijack threads with unrelated posts, especially when the thread you hijacked has been basically dead since August (the mods/admins really frown on that). If you have a Wine related sound problem, then search for and post in a topic that has something to do with Wine sound problems or create your own new thread. You'll be much more likely to get help that way.

---

### Post by DouglasAWh on 2007-11-07
I did: [http://ubuntuforums.org/showthread.php?t=605959](http://ubuntuforums.org/showthread.php?t=605959)

I have exactly zero responses...

the post talked about WINE, so when I searched I got here.

---

### Post by cogadh on 2007-11-07
You only posted that 5 hours ago, how quick did you expect to get a response? Last time I posted something in that forum I didn't get a response for two days.

---

### Post by drummerjamin on 2009-12-07
The libalut0 package fixes the sound issue but for some reason it alters the graphics in Regnum Online. What happens to me (and in all the other distributions I have tried) is that the water textures turn red blue green and red and it artefacts pretty badly. Did anyone else notice this?

---

### Post by Ferrat on 2009-12-07
are you running Ubuntu 9.04 or 9.10 ??
9.10 is reported having issues with RO, same goes for other "latest version" dists as well like SuSe and a few others, while earlier version like 9.04 on Ubuntu runs flawless, seems to be a missmatch somewhere that messes up a few things like sound and graphic.
I'm running RO under 9.04 and have everything on MAX and it's flawless :)

---

