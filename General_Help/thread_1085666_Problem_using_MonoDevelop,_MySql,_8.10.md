---
title: "Problem using MonoDevelop, MySql, 8.10"
date: 2009-03-03
forum: General Help
---

### Post by NiceCup OfTea on 2009-03-03
I'm having a problem getting monodevelop and MySql to play nicely.  I have done some googling and think the problem is that the libmysql5.0-cil that you get using synaptic is broken.  Messages imply that this is fixed in a later version '5.2.1-dfsg-2' (not sure what those runes mean) but there seem to be no suggestions on how to get this fix installed.

Is it possible OR do I have to go the whole hog and go to development versions of mono/monodevelop/MySql etc.

I'm trying to write a simple prog that uses ADO to access MySql and I get an error:  System.ArgumentException: Stream is not a valid .resources file, magic=0x6d783f3c.

Any ideas?

Thanks

---

### Post by carlosm7 on 2009-05-28
The bug is [_reported and fixed_]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=491407"), the version on Synaptic is the previous one, so I had to download the new one from [_elsewhere_]("http://packages.debian.org/lenny/all/libmysql5.0-cil/download"), and now I can connect to the database and make quieries, etc. just fine.

This fix is old, I wonder why it is still not in Synaptic.

---

### Post by directhex on 2009-05-28
> **carlosm7 said:**
> This fix is old, I wonder why it is still not in Synaptic.

Because once a release is out, it stops getting updates. Intrepid will not receive an updated package.

---

