---
title: "DVD+RW Burning Problems - solved? (Dapper)"
date: 2006-07-18
forum: Desktop Environments
---

### Post by SickIcarus on 2006-07-18
Hello everybody.

1st, a big THANK YOU to all the help I've received by perusing this forum. I've only been using Linux for less than 2 weeks now, and if it wasn't for the damned DVD-burning problem (I/O Error) I'd never boot into Windows again.

Well, after much perusal on these forums, but not much luck in finding a cure - although I've found a ton of threads on this - I think I got it licked. At least for me, anyways.

The latest version of DVD+RW Tools solved this for me. I haven't seen anything about this fix on these forums, so if its here and I missed it, well then, woops.

Grab dvd+rw-tools_6.1-2_i386.deb from the link below:
[http://packages.debian.org/unstable/utils/dvd+rw-tools]("http://packages.debian.org/unstable/utils/dvd+rw-tools")

Yes, its in the Unstable section. The Stable section only has the version installed with the standard repositories.

```
sudo dpkg -i dvd+rw-tools_6.1-2_i386.deb
```

Once I installed it, K3B hasn't missed a beat since.
I haven't noticed any adverse affects, despite its being labled Unstable.

Only thing I have had to do from time to time, if I put a DVD+RW disc in with stuff already on it, sometimes I have to right-click its icon on the desktop and Unmount it - otherwise K3B lets me know it couldn't unmount it.
A trifle compared to the non-stop IO Errors I was getting before.

Hope this helps!

---

