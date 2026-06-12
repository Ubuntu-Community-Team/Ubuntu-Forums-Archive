---
title: "Different resolution in dual monitor creates cursor &quot;blind spot&quot;"
date: 2009-07-06
forum: Desktop Environments
---

### Post by relix on 2009-07-06
Since this must be a common situation, I tried searching for similar questions but couldn't dig up anything, probably due to keyword-mismatch. I apologize in advance.

I have two monitors in a dual monitor setup: one which is 1920x1200 and one which is 1280x1024. Using TwinView this creates a "blind spot" of 1280x176 at the top of the smaller monitor where I can move the cursor but cannot see it.

Is there a way to keep the mouse from going into this area?

---

### Post by BbUiDgZ on 2009-07-06
> **relix said:**
> Since this must be a common situation, I tried searching for similar questions but couldn't dig up anything, probably due to keyword-mismatch. I apologize in advance.

I have two monitors in a dual monitor setup: one which is 1920x1200 and one which is 1280x1024. Using TwinView this creates a "blind spot" of 1280x176 at the top of the smaller monitor where I can move the cursor but cannot see it.

Is there a way to keep the mouse from going into this area?

you've went one better than me,
when i tried (back in 7.10) i couldnt get two screens to output to different resolutions. I gave up

---

### Post by relix on 2009-07-06
> **BbUiDgZ said:**
> you've went one better than me,
when i tried (back in 7.10) i couldnt get two screens to output to different resolutions. I gave up

It's easy on the latest versions of Ubuntu, just install the restricted drivers and use the configuration app (nvidia-settings if you've got Nvidia). It even works without reboot.

---

### Post by wojox on 2009-07-06
Have you tried increasing the resolution to take care of the blind spot?

---

### Post by relix on 2009-07-06
> **wojox said:**
> Have you tried increasing the resolution to take care of the blind spot?

My monitor doesn't support the resolution, nvidia-settings doesn't allow me to set it higher.

---

### Post by amites on 2009-12-05
any chance you could post your xorg.conf for the rest of us?

I just added a 22" to a former 17" dual (now 22" + 17") and getting frustrated

though I've learned enough along the way that I might be able to fix both of our issues

---

