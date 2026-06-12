---
title: "Loss of kubuntu-low-fat-settings"
date: 2014-04-25
forum: Desktop Environments
---

### Post by springshades on 2014-04-25
There isn't really a question here. I realize this change happened a while back, but I've stuck with the LTS releases. I was wondering why this package had been removed, so I used some google-fu to find out. I assumed that perhaps they lost the maintainer or something along those lines. Or perhaps the package was incompatible with some new project they had started up. Nope. It turns out that the removal of this package was to appease one guy who doesn't use Kubuntu (appears to be primarily Debian).

[http://bazaar.launchpad.net/~kubuntu-packagers/kubuntu-settings/kubuntu-settings/revision/548](http://bazaar.launchpad.net/~kubuntu-packagers/kubuntu-settings/kubuntu-settings/revision/548)

And this guy was apparently a KDE developer having a fit about the fact that the package turned off compositing.

[http://blog.martin-graesslin.com/blog/2013/05/](http://blog.martin-graesslin.com/blog/2013/05/)

Now to be fair, I also tended to turn compositing back on (and the few affects that I found useful) after installing this package. But it's much easier to install a package that gets rid of all of the crap and then turn back on the few things that you find useful than it is to figure out where all the crap is in the first place.

The end result of this is that, in my experience at least, the RAM usage of Kubuntu at idle went from ~200 MB in 12.04 to ~600 MB in 14.04. And at least as far as the interface goes, it's almost impossible to tell the difference between the two. I don't have much of a point, but I figured there must be a handful of people out there who wondered what had happened as well.

---

### Post by vasa1 on 2014-09-21
> **springshades said:**
> ...
[http://blog.martin-graesslin.com/blog/2013/05/](http://blog.martin-graesslin.com/blog/2013/05/)
...
This points to the relevant post: [http://blog.martin-graesslin.com/blog/2013/05/compositing-and-lightweight-desktops/](http://blog.martin-graesslin.com/blog/2013/05/compositing-and-lightweight-desktops/)
Although there's no mention of the dev asking for low-fat to be removed, the other link makes it clear. Pity.

---

