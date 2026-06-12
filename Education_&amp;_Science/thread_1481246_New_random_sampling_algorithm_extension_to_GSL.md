---
title: "New random sampling algorithm extension to GSL"
date: 2010-05-12
forum: Education &amp; Science
---

### Post by WebDrake on 2010-05-12
Hello all,

Following the very helpful discussion on the Programming Talk forum:
[http://ubuntuforums.org/showthread.php?t=1462257](http://ubuntuforums.org/showthread.php?t=1462257)

... and some subsequent research, I decided to prepare free software implementations of some of the sequential random sampling algorithms described in the last post of the earlier discussion.

This is being built as an [extension]("http://www.gnu.org/software/gsl/#extensions") to the [GNU Scientific Library]("http://www.gnu.org/software/gsl/") (GSL), but the longer-term aim is for it to be incorporated back into GSL proper after suitable review and testing, since it provides useful functionality that is not at present available.  One benefit of the present code is that it already provides a faster alternative to GSL's gsl_ran_choose sampling function, and will provide even faster alternatives in the near future ... :-)

Current development is taking place on GitHub at:
[http://github.com/WebDrake/GrSL/](http://github.com/WebDrake/GrSL/)

Contributions of code, review and feedback are all welcome, especially from people with sampling algorithm experience or expertise.  Particularly important will be the development of effective testing and review for the implementations of the different sampling algorithms.

Thanks & best wishes,

    -- Joe

---

