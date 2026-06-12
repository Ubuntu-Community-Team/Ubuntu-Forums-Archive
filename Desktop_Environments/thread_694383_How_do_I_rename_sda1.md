---
title: "How do I rename sda1?"
date: 2008-02-12
forum: Desktop Environments
---

### Post by bdtgp on 2008-02-12
I want to rename my Vista partition to say Windows instead of sda1 when I am in Ubuntu.  How do I do this?  Do I have to use ntfsprogs and force it or is there another way?

---

### Post by hardyn on 2008-02-12
well its not all that straight forward, but not all that difficult.
assuming that you have retained the UUID system, and have not staticly linked things...

you must add a new mount point (directory) to the /media directory, as apposed to sda1.  say /media/vista.  then you must change your automount file, fstab, to point to that new mount point.

I am not in front of my linux box right now, so i cannot test the instructions that i just provided, but that is how it is done, i have done it a few times.

---

