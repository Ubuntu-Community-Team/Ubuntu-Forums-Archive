---
title: "guake and guake-indicator are not compatible in bionic"
date: 2020-01-21
forum: Desktop Environments
---

### Post by belfeldt on 2020-01-21
Hello forum,
some time ago I've noticed the supplied packages for guake and guake-indicator are not working any more in bionic. Developers side says:
>     If you want to connect guake-indicator to Guake 3 you must use  version 1.3.1 and provide -guake3 as the first argument.     From version 1.3.2, Guake3 is the default shell so you don't have to  provide -guake3 switch, fallback to old Guake 0.x is still possibile  with the -guake0 switch. [http://guake-indicator.ozzyboshi.com/issues.html](http://guake-indicator.ozzyboshi.com/issues.html)
Provided packages in bionic are guake 3.0.5-1 and guake-indicator 1.1-2.

I'm certainly running late, prospecting a new LTS in a few months were this issue is probably eliminated. Meanwhile I've got the sneaking suspicion it's due to other unresolvable package dependencies. But is there any chance of remediation? Is this actually the right place for reporting such kind of bugs?

Appreciate any answer.

---

### Post by mörgæs on 2020-01-22
In 19.10 guake-indicator is version 1.4-1. A fresh install of this one is likely to solve the problem.

---

