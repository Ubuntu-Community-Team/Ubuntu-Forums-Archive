---
title: "ggplot doesn't show plots"
date: 2014-03-27
forum: Education &amp; Science
---

### Post by elexhobby2 on 2014-03-27
I tried the following simple code in R
```
library("ggplot2")
a = c(1,2,3,4)
b = 2*a
ggplot() +
   geom_line(aes(x=a,y=b))

```
The plot doesn't show up. If I add ggsave, the plot is saved, so I know the plot is being produced. It just doesn't show up in a plot window. 

I asked another friend to try out the code on his machine (also Ubuntu), and it worked. So I think its a problem with my R installation. Any ideas what's wrong?

Thanks!

---

### Post by Neil_Hollow on 2014-06-07
I know this not really a reply to your problem but have you considered using qtiplot?  I have had problems load modules in RKWard see my post above.

---

