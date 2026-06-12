---
title: "Windows Snapping to Invisible wall 1/2 Inch above AWN"
date: 2008-06-25
forum: Desktop Environments
---

### Post by willymcsilly on 2008-06-25
Title pretty much says it all, my windows are snapping to an invisible wall when they get to close to the AWN dock this is really bugging me and was hoping someone could tell me how to stop this from happening

---

### Post by moonbeam on 2008-06-25
> **willymcsilly said:**
> Title pretty much says it all, my windows are snapping to an invisible wall when they get to close to the AWN dock this is really bugging me and was hoping someone could tell me how to stop this from happening

My guess is that you're using compiz.

I'd suggest looking at this bug.

[https://bugs.launchpad.net/awn/+bug/164614](https://bugs.launchpad.net/awn/+bug/164614)

In general there is a reproducible issue with the compiz snap plugin.  I believe at one point in time wobbly also had an issue but that it was resolved.  There's a bug open for the snap plugin on the open compositing bug tracker (you can find it linked in the bug listed above).

---

### Post by willymcsilly on 2008-06-30
thanks that did the trick
all you have to do is disable the snap inverted under wobbly windows in Compiz

---

