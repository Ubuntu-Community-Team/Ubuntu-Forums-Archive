---
title: "When effects are enabled my drag-bar goes white."
date: 2009-01-28
forum: General Help
---

### Post by dragos240 on 2009-01-28
Ok so when i put my desktop effects on either normal or extra, the drag bar turns white. Help?

---

### Post by Gotaro on 2009-01-29
> **dragos240 said:**
> Ok so when i put my desktop effects on either normal or extra, the drag bar turns white. Help?
Are you talking about in Firefox?  Or in all apps?

---

### Post by zakany on 2009-01-29
I had that with the "Human" theme. Try one of the others and see if the problem persists.

---

### Post by dragos240 on 2009-01-29
> **zakany said:**
> I had that with the "Human" theme. Try one of the others and see if the problem persists.

Yup, it isn't happening in others, i wonder why?

---

### Post by zakany on 2009-01-30
Assuming you're running an Nvidia card on the 177 drivers, folks have reported that using the 180 series driver has fixed some things.

---

### Post by dragos240 on 2009-01-30
> **zakany said:**
> Assuming you're running an Nvidia card on the 177 drivers, folks have reported that using the 180 series driver has fixed some things.


Hmm...........  I don't see a 180 one, only 177, where can i get this.

---

### Post by zakany on 2009-01-31
> **dragos240 said:**
> Hmm...........  I don't see a 180 one, only 177, where can i get this.

Evidently, you can [click this]("apt:nvidia-glx-180") (from Ubuntu 8.10) and it ought to do the trick. I guess. :D Can't call myself a guru with an install and an hour of hoking around with the OS.

Anyway, that came from [this thread]("http://ubuntuforums.org/showthread.php?t=990978&highlight=180&page=44"). Before doing anything, I suggest reading through it since there seems to be quite a bit of disagreement on the virtues and pitfalls from one driver to another. 

:popcorn:

I believe that Nvidia lists 180.22 as the current driver version for Linux, but Ubuntu offers you 180.11 and neither fixes some known issues that are currently being addressed.

If I were you, I'd just do the apt:nvidia-glx-180 thing (linked above). Once I get my Ubuntu machine reassembled, I'll probably do the same.

---

### Post by dragos240 on 2009-01-31
> **zakany said:**
> Evidently, you can [click this]("apt:nvidia-glx-180") (from Ubuntu 8.10) and it ought to do the trick. I guess. :D Can't call myself a guru with an install and an hour of hoking around with the OS.

Anyway, that came from [this thread]("http://ubuntuforums.org/showthread.php?t=990978&highlight=180&page=44"). Before doing anything, I suggest reading through it since there seems to be quite a bit of disagreement on the virtues and pitfalls from one driver to another. 

:popcorn:

I believe that Nvidia lists 180.22 as the current driver version for Linux, but Ubuntu offers you 180.11 and neither fixes some known issues that are currently being addressed.

If I were you, I'd just do the apt:nvidia-glx-180 thing (linked above). Once I get my Ubuntu machine reassembled, I'll probably do the same.

Just downloaded the driver and installed it, but it's not fixing the bar glitch, although it's preforming a lot smoother.

---

