---
title: "R plotting: ggplot output differing from plot output for same dataset"
date: 2012-08-10
forum: Education &amp; Science
---

### Post by ganna10 on 2012-08-10
Hi,

I am starting to use R to create data plots using the ggplot2 package rather than the standard plot function that comes with R. 

The data is a set of mixing ratios of NO against time, hence very small values of NO but that change throughout the range of time values.

To get use the standard plot function I use:
plot(time, NO)

and the output is a plot that has maxima & minima throughout the plot.

To use ggplot I write:
ggplot(data=plot_data, aes(x=time, y=NO)) + geom_point() + coord_cartesian(ylim=c(0, 5e-12))

and the resulting output is a straight-line graph with all the y-values being 0.

I am just wondering now whether the fact that all the data input values for NO are in scientific notation (i.e. 6.6e-14).

Any help is appreciated!
Thanks,
Jane

---

### Post by PC_load_letter on 2012-08-10
Could you please elaborate more, what is NO? Also, can you attach the data set so I can try this on my setup and confirm the discrepancy if there is any?

Best.

---

### Post by ganna10 on 2012-08-13
NO is Nitrogen Oxide, the data is attached. 

Thanks,
Jane

---

### Post by PC_load_letter on 2012-08-14
Jane,
  It seems it's a bug in ggplot2, it doesn't scale correctly if the y-values are too small, it has been fixed in 0.9.0 but apparently it came back, here: 
[https://www.google.com/search?q=ggplot2+bug+small+values&sugexp=chrome,mod=15&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=ggplot2+bug+small+values&sugexp=chrome,mod=15&sourceid=chrome&ie=UTF-8)

There is a workaround by scaling your data, here:
```
s <- 1E15
ggplot(NO_time, aes(time, NO*s)) + geom_point() + scale_y_continuous(labels=function(x) as.character(x/s)) + ylab("Y")
```

With this code I get this plot which is the same as the one I get from the standard plot.

---

### Post by ganna10 on 2012-08-15
That is fantastic! Works like a charm :-)

---

