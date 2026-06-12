---
title: "Compiz problems"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by Chainer on 2007-11-27
Compiz/compiz-core no longer seems to be working for me.  I have it set on the highest setting (within the Appearance section).  I am no longer getting the window sticky type visuals (where the windows appear stick to the edges of the monitor when grabbed with the cursor).

I am kind of lost on really what to do.  I have tried uninstalling and reinstalling compiz, but to no avail.  I also tried uninstalling compiz and installing beryl, but that didn't work as well.  Beryl didn't work for me either!  I would much rather have compiz as it is the one still supported and installed with Ubuntu by default...

Any idea on what to do?

---

### Post by overdrank on 2007-11-27
> **Chainer said:**
> Compiz/compiz-core no longer seems to be working for me.  I have it set on the highest setting (within the Appearance section).  I am no longer getting the window sticky type visuals (where the windows appear stick to the edges of the monitor when grabbed with the cursor).

I am kind of lost on really what to do.  I have tried uninstalling and reinstalling compiz, but to no avail.  I also tried uninstalling compiz and installing beryl, but that didn't work as well.  Beryl didn't work for me either!  I would much rather have compiz as it is the one still supported and installed with Ubuntu by default...

Any idea on what to do?

Hi and if you installed beryl by adding feisty repos then that I believe is the cause of your issue. Remove or comment out the repo and then completely remove compiz-fusion and all associated apps then try again. hope this helps good luck!

---

### Post by Chainer on 2007-11-27
I tried this, and it did not work...

I mean, it's not a huge deal, but the visuals are sweet and one of the reasons I came to Ubuntu to the begin with...besides music management of course!  :)

Any other ideas?

---

### Post by -grubby on 2007-11-27
> **Chainer said:**
> I tried this, and it did not work...

I mean, it's not a huge deal, but the visuals are sweet and one of the reasons I came to Ubuntu to the begin with...besides music management of course!  :)

Any other ideas?

try deleting you ./compiz folder under home/username and uninstalling and then reinstalling compiz

---

### Post by Chainer on 2007-11-27
That worked!  Thanks!

---

