---
title: "Suspend/Hibernate Problem"
date: 2009-01-15
forum: General Help
---

### Post by sprince09 on 2009-01-15
I have been using Ubuntu 8.10 since release day on my Gateway M6862 laptop. Pretty much everything works, but I have run into a few problems because my video card (ATI mobile Radeon 3600) is, well, an ATI card. I've found work arounds for most of the issues I've had so far, but I'm stuck on one.

The problem:
Suspend and hibernate both work (they sucessfully suspend/hibernate my computer), but when I try to resume, I get one of the following problems:
-Black screen with mouse frozen.
-Login box displays normally but is frozen
-Login box displays as only a grey box

This happens whenever I have the "Visual Effects" checked to anything except "None" in the System->Apperance->Visual Effects menu. I would like to be able to use at least the lowest teir of effects on this computer (they are pretty :) ).

To reiterate that point: suspend/hibernate works perfectly if I disable visual effects.

I'm running the latest proprietary fglrx drivers.

Anyway, what I'd like to do is modify the suspend/hibernate and resume scripts to disable and re-enable these effects at the proper time to prevent my system from locking up. How would I do this?

---

