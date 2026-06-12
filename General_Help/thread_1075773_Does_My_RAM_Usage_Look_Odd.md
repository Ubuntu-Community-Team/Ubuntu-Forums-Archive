---
title: "Does My RAM Usage Look Odd?"
date: 2009-02-20
forum: General Help
---

### Post by Mark76 on 2009-02-20
I seem to be using a lot for very little

---

### Post by mcduck on 2009-02-20
could you run "free -m" in a terminal and post the output here? (that will give a lot easer-to-read results than what your screenshot provides..)

---

### Post by Mark76 on 2009-02-20
I'm thinking FF is using way too much.

Why is that?

> free -m
             total       used       free     shared    buffers     cached
Mem:           873        853         20          0         20        217
-/+ buffers/cache:        615        258
Swap:         2557          5       2552


---

### Post by mcduck on 2009-02-20
That doesn't look too horrible, although you are indeed using quite a lot of RAM.

Firefox can be quite a memory hog if left running for long times or having many pages open at the same time. Not to mention what happens if pages have Flash or other resource-intensive content, or if you have many extensions installed in Firefox.

Sadly, it's just not the lightweight browser it used to be. I suppose that's the price we have to pay for having all the fine features.

---

### Post by Mark76 on 2009-02-20
I've tried the lighter graphical browsers like Kazehakase and Midori, but they're all deficient in some way :(

---

