---
title: "hovmuller diagrams"
date: 2011-05-20
forum: Education &amp; Science
---

### Post by Senplanet on 2011-05-20
Does anybody know any freeware running on ubuntu which can plot hovmuller diagrams from ASCII file,please?
I know that Matlab can do it, but I am looking for something free...
Also some link for example script could be great.
Thanks for suggestions~

---

### Post by sisyphus1978 on 2011-05-20
Never heard of hovmuller, but a quick google shows me that R (maybe search for the clim.pact package) and gnuplot may be able to produce them. 

Good luck.

---

### Post by Senplanet on 2011-05-21
Hello, 
I have some experience with gnuplot, and I think there is not such a way to do hovmuller plot. However I have hope in R. Thanks for your idea. I will try it.

---

### Post by sisyphus1978 on 2011-05-25
Did you have any luck with this? I have found R a very useful package to use. :)

---

### Post by Senplanet on 2011-05-30
Well, I tried R, but its quite complicated to figure out the way how the plot the hovmuller without any example script. Finally, I plot it as a contour map with GIS program called Surfer. But this is Windows application. So I had to skip to my old XP for a while. However the plot looks nice. But I still would like to know how to do it with some computing tool such as R under linux, so I can create script and run it from terminal. Please if you have anything that can help, just let me see.
Thanks

---

### Post by sisyphus1978 on 2011-05-30
The plotField documentation gives an example, but I haven't got time to try and get it running. I always have good luck over at stackoverflow.com. You could try over there.
```
## Don't run: 
skt <- retrieve.nc("skt.mon.mean.nc",x.rng=c(-90,50),y.rng=c(0,75))

# Maps of monthly mean skin temperatures:
plotField(skt,tim=1,val.rng=c(-20,20))
dev2bitmap("ncep.skt_194801.jpg",type="jpeg")

plotField(skt,tim=100,col="blue",col.coast="darkgreen",val.rng=c(-10,10))

# For adding extra points/contours:

    # From filled.contour in base
    mar.orig <- (par.orig <- par(c("mar","las","mfrow")))$mar
    on.exit(par(par.orig))

    w <- (3 + mar.orig[2]) * par('csi') * 2.54
    layout(matrix(c(2, 1), nc=2), widths=c(1, lcm(w)))
   
    par(las = 1)
    mar <- mar.orig
    mar[4] <- 1
    par(mar=mar)
# End of section affecting the window set up.

points(0,50,pch=21,col="red")
grid()
dev2bitmap("ncep.skt_195604.jpg",type="jpeg")

# A hovmuller diagram:
plotField(skt,lon=0,val.rng=c(-10,10))
dev2bitmap("ncep.skt_lontim.jpg",type="jpeg")

# A single time series:
plotField(skt,lon=-20,lat=50)
```

## End Don't run

---

