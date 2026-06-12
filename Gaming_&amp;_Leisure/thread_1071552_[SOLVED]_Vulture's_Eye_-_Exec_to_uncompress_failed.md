---
title: "[SOLVED] Vulture's Eye - Exec to uncompress failed"
date: 2009-02-16
forum: Gaming &amp; Leisure
---

### Post by amrbekhit on 2009-02-16
Hello all,

I managed to successfully compile Vulture's Eye on Ubuntu 8.10. The game seems to run fine and I played it for quite some time. Then I came to save and quit and the game froze. A look at console output shows the following message:

```
Exec to compress save/1000Amriun failed.
```

Likewise, if I try to load a game, I get:

```
Exec to uncompress save/1000Amriun failed.
```

Any ideas?

Thanks

--Amr

---

### Post by amrbekhit on 2009-02-16
Damn it! As soon as I posted the message I fixed it - I needed to install ncompress. All good now!

---

### Post by j3gorman on 2009-03-11
Thanks for the post; I had the same problem with saving games in Vulture's Eye and your solution was the fix I needed.

I have to ask; how did you come up with the fix? How did you know that ncompress was needed?

Thanks again!

---

### Post by amrbekhit on 2009-03-12
Hi j3gorman,

Glad to hear that you also got the game working. Unfortunately, it's been several weeks since the problem and I can't remember exactly how I solved it. However, it will have involved running the game through the terminal so that I could read the error messages and then do some google searches. I do remember looking for the save game files in the game directory and noticing that the game tried to create .Z files for the save games. That will have factored into the searches.

Happy nethacking!

--Amr

---

