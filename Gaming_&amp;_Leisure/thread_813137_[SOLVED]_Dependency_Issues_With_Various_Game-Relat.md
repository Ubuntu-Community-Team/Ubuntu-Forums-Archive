---
title: "[SOLVED] Dependency Issues With Various Game-Related Packages"
date: 2008-05-30
forum: Gaming &amp; Leisure
---

### Post by RKCole on 2008-05-30
Hello, everyone.

I have been attempting to install various packages, but each of them seem to have dependency problems.  Additionally, they all seem to deal with libcairo2 and/or libpango1.0-0.  For instance, when trying to install [Mupen64Plus]("http://getdeb.net/app/Mupen64Plus") from GetDeb, I receive the following dependency issues:

```

Unpacking mupen64plus (from mupen64plus_1.3-1~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of mupen64plus:
 mupen64plus depends on libcairo2 (>= 1.6.0); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 mupen64plus depends on libpango1.0-0 (>= 1.20.1); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.
dpkg: error processing mupen64plus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mupen64plus

```

Now I'm still learning here in the Linux world, and I'm not quite sure how I can resolve these issues.  Any help would be greatly appreciated. 

I am running Ubuntu 7.10.

Thanks for any assistance.

Please take care.

---

### Post by DoktorSeven on 2008-05-30
The version you downloaded (in fact, the only version there) is for Hardy Heron, Ubuntu 8.04.  You are getting dependency errors because your older version of Ubuntu does not have the newer versions of libraries that the package was built on.  

You need to either hunt down a version built on 7.10, build it yourself, or update to 8.04.

---

### Post by RKCole on 2008-05-30
Thank you, DoktorSeven.

I had my suspicions about the packages being for Hardy, but I was second guesing myself on that.  I should have taken a closer look at GetDeb, in particular this line at the top:

```

You are browsing software for Ubuntu Hardy (32 bits)

```

I guess that I just overlooked it.

In any case, I received my Hardy CD from ShipIt recently, so I guess I'll be utilizing it here very soon. :)

Many thanks.

Take care.

---

