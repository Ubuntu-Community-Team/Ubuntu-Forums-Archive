---
title: "Java update in Hardy repos"
date: 2008-11-11
forum: Desktop Environments
---

### Post by vitorg on 2008-11-11
There is new Java released 6u10 that has fix for Compiz+Java incompatibility (see [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775)).
And there is no actions from Ubuntu developers to update Java in Hardy. Please, vote for this bug at [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/288658](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/288658)

---

### Post by Vadi on 2008-11-11
Can't vote, but can click on "This bug affects me too" :)

I've let guy who packages wine for ubuntu know about this, hopefully he'll be able to bring it to the proper authority

---

### Post by jamesstansell on 2008-11-11
I haven't done it with this release, but I in the past I have grabbed the sun-java6* packages from a newer ubuntu release and installed them manually on the older release that I was still running.  Then synaptic shows them as something like "obsolete or locally installed."

The times I've done that I haven't had any problems.

If you do it with 6u10, though, you should be aware that people are reporting regressions with the "classic" oji plugin - seeing browser hangs.  The new plugin2 that Sun shipped in 6u10 seems to be fine though.  (But the packaging so far doesn't allow you to enabled it as easily as the other plugins.)

This is just a possible work-around for people still on hardy who want 6u10 right now.  Feel free to add your vote to the bug.  :)

-james.

---

