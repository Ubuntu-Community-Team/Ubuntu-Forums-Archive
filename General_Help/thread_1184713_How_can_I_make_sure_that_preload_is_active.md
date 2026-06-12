---
title: "How can I make sure that preload is active?"
date: 2009-06-11
forum: General Help
---

### Post by DouglasCaixeta on 2009-06-11
Hi,

I install preload, but when I look on Sessions there is nothing there. Services as well, no preload.
How can I make sure that preload is really working?

I can handle Firefox anymore. Is too slow to load!

---

### Post by jimv on 2009-06-11
If you installed preload, it's active.  That said, Firefox always loads slow.  You could try another browser like Opera, which is faster.

[http://www.opera.com/](http://www.opera.com/)

---

### Post by DouglasCaixeta on 2009-06-11
Opera is faster cause they have a specific preload for it. Stays on tray all the time. The problem is that some websites dont like Opera.

---

### Post by jimv on 2009-06-11
Some websites don't like Firefox.  That said, Opera scores the highest on the Acid3 test compared to any other browser.

---

### Post by sdennie on 2009-06-11
You can verify that preload is running by doing:

```

sudo cat /var/log/preload.log

```

It takes some time for it to learn what should be preloaded so, if you've only just installed it, wait for a few days.

---

### Post by DouglasCaixeta on 2009-06-11
Thanks! That it was i need :)

---

