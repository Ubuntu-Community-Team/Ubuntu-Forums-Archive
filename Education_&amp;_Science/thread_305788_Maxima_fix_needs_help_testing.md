---
title: "Maxima fix needs help testing"
date: 2006-11-23
forum: Education &amp; Science
---

### Post by LaserJock on 2006-11-23
Hello,

  We **finally** have a fix for the awful maxima frontend breakage in 6.06 (dapper). We need people to test the fix before it is uploaded to dapper-updates. What you need to do is add:
```
deb http://archive.ubuntu.com/ubuntu/ dapper-proposed main universe
```
to your apt sources (/etc/apt/sources.list) and then update. The 2 packages that are specifically needed are gcl and maxima. If you test this out (making sure a maxima GUI like xmaxima or wxmaxima work) please add a comment to [https://launchpad.net/distros/ubuntu/+source/wxmaxima/+bug/43150](https://launchpad.net/distros/ubuntu/+source/wxmaxima/+bug/43150)

Thanks.

-LaserJock

---

