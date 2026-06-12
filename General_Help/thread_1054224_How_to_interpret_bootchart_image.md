---
title: "How to interpret bootchart image?"
date: 2009-01-29
forum: General Help
---

### Post by sceo on 2009-01-29
I'm not exactly fluent in Gantt Chart so trying to use bootchart to identify why my startup takes a while is eluding me.  Can anyone identify what might be some of the problems?

One thing that looked somewhat odd to me was a "find" process, but still - perhaps there's some valid need for that.

First off, I don't know what I'm looking for as "culprits" for my slow boot time, and secondly, I don't know what a lot of these processes are so I assume they're needed.  (I know I could get rid of, say, apache on boot - but it's not really being a time hog in the scheme of things it seems).

---

### Post by cros13 on 2009-02-09
*BUMP*

Looks like find/mysql are ramping up your disk usage.

Do you need mysql and exim?

Attaching my bootchart just to sicken you ;)

---

