---
title: "mathematica plotlegend problem"
date: 2009-01-21
forum: Education &amp; Science
---

### Post by Berto88 on 2009-01-21
Hi,

im using mathematica to produce a plot with a legend. When i used the code below, it works fine on a pc a uni however when i try it at home the legend only has 1 line. The uni pc has windows mathematica 6, at home im using linux mathematica 6.

```
Plot[r, {z, 0, 2}, 
 PlotStyle -> {PointSize[Large], Dashing[Medium], Dashing[Small], 
   Dashing[Large], Thick}, 
 PlotLegend -> {"\!\(\*SubscriptBox[\"\[CapitalOmega]\", \
\"NR\"]\)=0", 
   "\!\(\*SubscriptBox[\"\[CapitalOmega]\", \"NR\"]\)=0.25", 
   "\!\(\*SubscriptBox[\"\[CapitalOmega]\", \"NR\"]\)=0.5", 
   "\!\(\*SubscriptBox[\"\[CapitalOmega]\", \"NR\"]\)=0.75", 
   "\!\(\*SubscriptBox[\"\[CapitalOmega]\", \"NR\"]\)=1"}, 
 AxesLabel -> {"z", "\!\(\*SubscriptBox[\"r\", \"e\"]\)"}, 
 LegendSize -> 1]
```

---

