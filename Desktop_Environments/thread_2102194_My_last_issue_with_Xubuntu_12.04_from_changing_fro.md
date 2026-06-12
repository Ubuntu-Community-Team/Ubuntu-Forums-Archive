---
title: "My last issue with Xubuntu 12.04 from changing from Ubuntu 10.04."
date: 2013-01-06
forum: Desktop Environments
---

### Post by mikodo on 2013-01-06
If I knew how to be more descriptive in the title/thread, I would. I fully expect to get  roasted here for not being descriptive enough. But, without writing a freakin book on my question, that no one will read, here is my non-descriptive question.

I use compiz, in Gnome2 Ubuntu 10.04, with no problems, that  I will relate I have with Xubuntu 12.04.

In Xubuntu 12.04, I use:

Compiz and use the negative feature (inverse) extensively as I do in Ubuntu 10.04.

Docky. I mentioned it just because I use it.

Nautilus, just for the FM, no desktop drawing.

**OK, the question, for Xubuntu 12.04:**

When I open a negative window in Xubuntu 12.04, from clicking on the panel or switching from another non-negative window, instead of nice crisp transition to the new negative window, I usually get a quick flash of light before going in negative mode, as if the the window was not in inverse (compiz negative mode), initially. This does not happen in Ubuntu 10.04.

I also notice a quick flickering before changing to a new page even without the CCSM negative. When I choose Xfwm as the window manager instead of compiz, this behavior does not happen. So, it is Compiz related in Xubuntu 12.04, but doesn't happen with Ubuntu 10.04.

My intel graphics are fast enough to not cause this behavior. I have tried a lot of different settings in CCSM, too many to mention, to no avail, though it might be a CCSM setting, I haven't tried yet.

Has anyone experienced this, and know how to fix it.

Thanks.

---

### Post by mikodo on 2013-01-07
Now that the developer of Compiz has been reported to have said he will only maintain compiz and not develop it anymore, I think I am just going to use xcalib for inverse/negative screens. I don't use compiz for anything else. Too bad, I liked compiz for linux, made it unique.

```
xcalib -i -a
```
Thanks.

;p

---

