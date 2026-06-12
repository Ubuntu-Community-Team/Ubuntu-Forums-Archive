---
title: "GraphViz/Dot: Arrow drawn incorrectly"
date: 2011-02-15
forum: Education &amp; Science
---

### Post by McFly81 on 2011-02-15
Hi there,

I have created a rather simple DOT-File:

```
digraph test {
    node [shape="box", fontsize=12]
    edge [fontsize=12]

    subgraph cluster_t1 {
        graph [label="1. Beobachtungstermin", style="filled", fillcolor="lightgray", fontname="arial", fontsize="10"]
        termin1 [label="Basiswert schließt auf oder\nüber der Rückzahlungsschwelle"]
        ende1 [label="Vorzeitige Rückzahlung:\nRückzahlungsbetrag 1", color="firebrick", fontcolor="firebrick"]
        termin1 -> ende1 [label="JA", color="firebrick", constraint=false]
    }

    subgraph cluster_t2 {
        graph [label="2. Beobachtungstermin", style="filled", fillcolor="lightgray", fontname="arial", fontsize="10"]
        termin2 [label="Basiswert schließt auf oder\nüber der Rückzahlungsschwelle"]
        ende2 [label="Vorzeitige Rückzahlung:\nRückzahlungsbetrag 2", color="firebrick", fontcolor="firebrick"]
        termin2 -> ende2 [label="JA", color="firebrick", constraint=false]
    }

    subgraph cluster_t3 {
        graph [label="3. Beobachtungstermin", style="filled", fillcolor="lightgray", fontname="arial", fontsize="10"]
        termin3 [label="Basiswert schließt auf oder\nüber der Rückzahlungsschwelle"]
        ende3 [label="Vorzeitige Rückzahlung:\nRückzahlungsbetrag 3", color="firebrick", fontcolor="firebrick"]
        termin3 -> ende3 [label="JA", color="firebrick", constraint=false]
    }

    termin1 -> termin2 [label="NEIN"]
    termin2 -> termin3 [label="NEIN"]
}
```

There are three red arrows in the graph; the manual of dot/graphviz says that the label of an edge is centered. But as you can see it is not (in two of three). If you look at the last of the arrows, the edge is not drawn from Boxborder to Boxborder, but instead from the inner part of the Box to the border of the other. And there, the label is centered.
As I see it, my syntax for the three edges is identical. Do you know why they are not drawn the same way? PNG-File is attached.

Thanks,
Chris

---

