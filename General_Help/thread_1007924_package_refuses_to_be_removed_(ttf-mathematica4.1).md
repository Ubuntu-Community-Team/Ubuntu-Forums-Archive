---
title: "package refuses to be removed (ttf-mathematica4.1)"
date: 2008-12-10
forum: General Help
---

### Post by d0.fnal on 2008-12-10
Hi,

I have tried to install a package called ttf-mathematica4.1 but it did not install properly. Since then, whenever I use apt-get or Synaptic to install or remove a package, the job is done, for those packages, and I keep getting this error:

```
(Reading database ... 104073 files and directories currently installed.)
Removing ttf-mathematica4.1 ...
W: /usr/share/fonts/truetype/mathml/math4b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3m__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math4mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2m__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math4___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math4m__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1m__.ttf: not registered.
dpkg: error processing ttf-mathematica4.1 (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 ttf-mathematica4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

How may I solve this annoying issue?

---

### Post by d0.fnal on 2008-12-10
Solved [here]("http://ubuntuforums.org/showthread.php?t=990622&highlight=ttf-mathematica4.1")
I will search next time. But it was really annoying!

---

