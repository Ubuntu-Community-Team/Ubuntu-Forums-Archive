---
title: "vertical panel shadows start button"
date: 2012-05-24
forum: Desktop Environments
---

### Post by anaconda on 2012-05-24
I moved xubuntus bottom panel to the left side and disabled the autohide. (Which is how I would like to keep it)

Now the vertical panel is on top of the top panel, and I cant press the "start" button on the top panel.
Actually if I click somewhere on the top panel it will raise to be to highest panel, and then I can press the "start" button. Until I click on the vertical panel again.

Is there any easy way to solve this problem?

I would like to be able to press the "start" button anytime I want....

---

### Post by rai4shu2 on 2012-05-24
Try changing the settings for your vertical panel (unlock it, change the length, whether it automatically increases length, etc.).

---

### Post by anaconda on 2012-05-24
Yep. that worked. Thanks.

If the panel is not long enough to overlap there is no problem.
But what if someone would like to have full lenght vertical panel in xubuntu?

is it not possible to set top-panel to always be above the vertical panel?

---

### Post by rai4shu2 on 2012-05-24
If you wanted a full height vertical panel, it wouldn't really make sense to have a full length horizontal panel. It's one or the other, I would think.

---

### Post by ndrwrd on 2012-05-25
There is a patch in xfce bugzilla fixing that panel overlap:

[https://bugzilla.xfce.org/show_bug.cgi?id=8627](https://bugzilla.xfce.org/show_bug.cgi?id=8627)

If you set the length of a vertical panel to 100%, it will fill the whole available screen height minus any horizontal panels.

---

### Post by anaconda on 2012-05-27
Great. 
That is how I would like it to work!

Do you know if this pach is coming as an update sometime, or do I have to compile it myself

---

