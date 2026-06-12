---
title: "PDF on top of histogram"
date: 2011-02-18
forum: Education &amp; Science
---

### Post by R33D3M33R on 2011-02-18
I would like to plot 2  histograms with pdf's on top of the histogram, but i get the picture as  shown in attachment. So, what's wrong with the pdf's? If i draw them on  separate graph, everything works. Thanks for the help in advance!

Here is the code:

```

par(mfcol=c(2,1))

h1 <- hist(Data$V1,scale="frequency", col="darkgray", xlab="Time per km")
.x <- seq(min(0), max(5), length=100)
g1 <- length(Data$V1)*dgamma(.x, shape=1.312491, scale=0.795368)
remove(.x)
lines(g1,col="red")

h2 <- hist(Data$V1,scale="frequency", col="darkgray", xlab="Time per km")
numSummary(Podatki[,"V1"], statistics=c("mean", "sd", "quantiles"), 
  quantiles=c(0,1))
.x <- seq(min(0), max(5), length=100)
g2 <- length(Data$V1)*dgamma(.x, shape=2.632, scale=1.59542)
remove(.x)
lines(g2,col="purple")

```


[[IMG]http://img218.imageshack.us/img218/9622/histb.png[/IMG]]("http://imageshack.us/photo/my-images/218/histb.png/")

---

