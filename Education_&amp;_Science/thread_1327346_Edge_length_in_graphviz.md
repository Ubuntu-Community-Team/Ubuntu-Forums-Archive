---
title: "Edge length in graphviz"
date: 2009-11-15
forum: Education &amp; Science
---

### Post by bonzi on 2009-11-15
Is it possible to specify the edge length in dot?? I tried weight but it is not working.

---

### Post by cfogelberg on 2010-06-29
Hi bonzi,

Without more detail on what you are trying to do it's hard to help, but you could try nodesep:

```
digraph G {
        nodesep=0.5;
        rankdir=LR;

        {
        rank = same;
        $n_1$(2);
        $n_2$(2);
        $n_3$(2);
        }

        $n_2$ -> $n_1$;
        $n_2$ -> $n_3$;
}
```

HTH,
Christo

---

