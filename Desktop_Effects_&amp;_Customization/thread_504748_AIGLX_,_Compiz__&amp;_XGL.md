---
title: "AIGLX , Compiz  &amp; XGL"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by gopoo on 2007-07-19
How compiz-fusion & AIGLX interconnected ?

I am just wondering the flow or renderign pipeline.

Is it something like

X.org -> AIXGL -> GTK -> Compiz -> Display ??

How significantly they are interconnected to each other ?

Any links ?

Thanks.

---

### Post by Happy_Man on 2007-07-19
AIGLX needs X.Org, GTK also needs X.Org, but Compiz needs hardware acceleration like AIGLX to run.

---

