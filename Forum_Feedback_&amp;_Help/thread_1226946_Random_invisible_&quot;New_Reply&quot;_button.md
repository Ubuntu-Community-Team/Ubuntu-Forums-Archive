---
title: "Random invisible &quot;New Reply&quot; button"
date: 2009-07-30
forum: Forum Feedback &amp; Help
---

### Post by schauerlich on 2009-07-30
The screenshot program makes the cursor invisible, but the button is a few pixels northwest of the tooltip. Clicking it brings you to a new reply page. I've found it on many threads. I don't believe this was intentional, so maybe an admin would like to remove it? Or it can be a nice little easter egg for those who don't read this thread.

[http://img115.imageshack.us/img115/4109/newreply.png](http://img115.imageshack.us/img115/4109/newreply.png)

---

### Post by jpeddicord on 2009-07-30
There was a thread on it a long time ago about it I think. The bottom section of the New Reply button stretches across the page.

---

### Post by Joeb454 on 2009-07-30
> **jacobmp92 said:**
> There was a thread on it a long time ago about it I think. The bottom section of the New Reply button stretches across the page.

Have we ever found out why that is?

---

### Post by jpeddicord on 2009-07-30
> **Joeb454 said:**
> Have we ever found out why that is?

Looks like the New Reply button (and children elements) are block level, which makes some elements span their maximum width depending on certain factors. There's some fancy HTML that makes the button look rounded, and it's not the standard CSS border-radius stuff. Meh, weird.

---

### Post by Bodsda on 2009-07-30
I found it back in August of '08, seems the consensus was FF and its bad HTML rendering

[http://ubuntuforums.org/showthread.php?t=884794](http://ubuntuforums.org/showthread.php?t=884794)

---

### Post by schauerlich on 2009-07-30
> **Bodsda said:**
> I found it back in August of '08, seems the consensus was FF and its bad HTML rendering

I'm using Safari 4.0.2. So it's not just FF and/or Gecko.

---

### Post by Bodsda on 2009-07-30
> **EDavidBurg said:**
> I'm using Safari 4.0.2. So it's not just FF and/or Gecko.

Seems like only opera are doing it 'right' then

---

### Post by jpeddicord on 2009-07-30
> **Bodsda said:**
> Seems like only opera are doing it 'right' then

Or maybe they're doing it wrong and the other browsers are rendering the quirk correctly? ;)

---

### Post by Bodsda on 2009-07-31
> **jacobmp92 said:**
> Or maybe they're doing it wrong and the other browsers are rendering the quirk correctly? ;)

Interesting suggestion, of course, the real test would be too see how w3m or links2 rendered it. I doubt they would even recognize it.

---

