---
title: "Kubuntu 11.10 on Dell Studio 1558 -- suspend issues"
date: 2011-10-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Alex_W on 2011-10-11
Hi all,

Possibly a stupid question, read at your own risk ;-)

Kubuntu 11.10 beta 2 with latest upgrades; stock kernel with a parameter "acpi_backlight=vendor". Suspend-resume (and brightness -- but that's a different topic) works as expected when a user is logged in, but not when logged out... Has anyone else encountered that? Possible solutions?

Thanks,'

Alex

PS. As a side question: can't make the laptop boot with 3.0.6, 3.0.5, 3.0.4 etc. kernels from Mainline PPA... anyone has been able to?

---

### Post by Alex_W on 2011-10-16
Really? No one encountered this with the Oneiric? (on the other hand, I've been Google-searching this for several days now... -- no luck; and no reports on Launchpad).

So, forget the brightness issue (for now), and the kernel thing.

Dell Studio 1558 (i3, Intel graphics). Tried Kubuntu 11.10 32- and 64 bit, and Ubuntu 64 bit. Suspend-resume only works if a user is logged in. If a user is **not** logged in (i.e., you have the "Welcome" screen on the monitor), closing the lid doesn't even turn the monitor off.

10.04 works just fine* (brightness issue fixed by [**Kamal's kernel patch**]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611")

I'm honestly not even sure how to debug this... since one has to be logged out of the system to see this behavior...

...help?..

---

