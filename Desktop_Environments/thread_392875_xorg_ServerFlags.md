---
title: "xorg: ServerFlags"
date: 2007-03-25
forum: Desktop Environments
---

### Post by newbie22 on 2007-03-25
What is the difference between all the below Options?:

"blank time"
"standby time"
"suspend time"
"off time"

The above terms are synonymous to me.

If I want my monitor to go to sleep mode which Option am I suppose to edit?  By "sleep mode" I mean by monitor goes black after a certain inactive amount of time.  Should I move the mouse or hit a key, it would restore to the previous state.

And what format should the entry be in?  For example: "1 hour"  Should I enter it as "1 hour", "1:00", "60 minutes", or "60"?

---

### Post by adam.tropics on 2007-03-25
> **newbie22 said:**
> What is the difference between all the below Options?:

"blank time"
"standby time"
"suspend time"
"off time"

The above terms are synonymous to me.

If I want my monitor to go to sleep mode which Option am I suppose to edit?  By "sleep mode" I mean by monitor goes black after a certain inactive amount of time.  Should I move the mouse or hit a key, it would restore to the previous state.

And what format should the entry be in?  For example: "1 hour"  Should I enter it as "1 hour", "1:00", "60 minutes", or "60"?

An example would be:
```
Option     "blank time"    "10"    # 10 minutes
```

---

