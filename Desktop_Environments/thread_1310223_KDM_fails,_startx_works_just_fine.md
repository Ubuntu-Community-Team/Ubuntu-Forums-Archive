---
title: "KDM fails, startx works just fine"
date: 2009-11-01
forum: Desktop Environments
---

### Post by ltmon on 2009-11-01
As per subject.

When I start up, the nvidia splash shows and then the X server crashes. This repeats itself a bit, but ultimately I get a console login.

After logging in from console, I can simply type "startx" and have a desktop up and running with no problems.

I have tried recreating my KDM configuration from scratch (see README in /etc/kde4/kdm/) but to no avail.

My KDM log (/var/log/kdm.log) has no error lines (EE), but abruptly ends with:

```

ddxSigGiveUp: Closing log

```

After this I can see debconf trying to show a console dialogue (failing) and /etc/gdm/failsafeXServer trying to launch (failing and segfaulting). Full log is at [http://pastie.org/679397](http://pastie.org/679397)

I'm using up to date Karmic (upgraded from 9.04, upgraded from 8.10 upgraded from etc. etc...). I have installed the latest nvidia drivers (190.42) from nvidia bin packages.

I've also just noticed that I can do the following at my console:
```

# sudo stop kdm
# sudo start kdm

```

and get a perfectly functioning KDM working. So it's only on initial startup that it fails.

Any ideas?

Thanks,

L.

---

### Post by ltmon on 2009-11-04
For future searchers, I solved this one.

There are artifacts of old packages remaining around. Specifically bits and pieces of kdm-kde4 (a transitional package) and kde-guidance (more worrying as it was part of base install).

Finding and removing all the remainders of these packages fixed the problem.

---

