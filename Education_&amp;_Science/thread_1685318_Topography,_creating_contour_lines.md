---
title: "Topography, creating contour lines"
date: 2011-02-10
forum: Education &amp; Science
---

### Post by Greg Rabbit on 2011-02-10
Hello !

I am searching for open source program related to topography.

Specifically i am interest to find a program that can create contour lines and 3d terrain from x,y,z points.
Meaning to be given data as x,y,z coordinates and with these data create contour lines and preferably model them in a 3d terrain. The best thing is if it could also measure volumes of these 3d areas.

I am a civil engineer and the non open source similar programs are things like terraincad and autocad civil, yet I would like to find an open source similar option.

Best greetings!
Greg

---

### Post by hzambran_cl on 2011-02-10
Besides GIS programs, you may try with R:

[http://addictedtor.free.fr/graphiques/search.php?engine=RGG&q=contour]("http://addictedtor.free.fr/graphiques/search.php?engine=RGG&q=contour")

---

### Post by hubie on 2011-02-10
I was going to suggest R as well, but using the [misc3d]("http://cran.r-project.org/web/packages/misc3d/index.html") package.  The contour3d function will take in x, y, and z values and will make contours.  I'm not sure what kind of interaction you want with it, but it wouldn't be too hard (says the guy who doesn't need to :) ) to write a function to calculate volumes.

---

### Post by Greg Rabbit on 2011-02-11
Hey, thanks to both for the fast reply.

I am currently experimenting with Saga and Qgis to make this work.
And now I will take the courage to take the question to the ... next level!

Is there somewhere online a good clear step by step tutorial on how to do this.
this = 
- creating contour lines from x,y,z data, 
- create 3d terrain based on these contour lines
- measuring volume of this terrain.

I would really appreciate a good clear tutorial on this. The software can be either qgis, saga, grass, or whatever you think that works and I can download easily,
My operating systems are windows xp, windows 7 and ubuntu.

Thanks!!!!!!!!!!!
Greg

---

### Post by hzambran_cl on 2011-02-11
In R, you can read the help page of the 'contour' command, and in particular the examples section:

> ?contour

as an example:

```
x <- 10*(1:nrow(volcano)); x.at <- seq(100, 800, by=100)
y <- 10*(1:ncol(volcano)); y.at <- seq(100, 600, by=100)

image(x, y, volcano, col=terrain.colors(100),axes=FALSE)
contour(x, y, volcano, levels=seq(90, 200, by=5), add=TRUE, col="brown")
axis(1, at=x.at)
axis(2, at=y.at)
box()
title(main="Maunga Whau Volcano", sub = "col=terrain.colors(100)", font.main=4)
```

---

### Post by HydrologyGuy on 2011-02-13
All of the recomended programs (Qgis, SAGA, GRASS, R) are useful. However if you want to automate the process without learning R, you could also try GMT (Generic Mapping Tools). It's essentially a command-line driven GIS. It has a wide variety of utilities including grdvolume which can "calculate volumes under a surface within specified contour" according to the manual.

---

### Post by hubie on 2011-02-14
> **HydrologyGuy said:**
> All of the recomended programs (Qgis, SAGA, GRASS, R) are useful. However if you want to automate the process without learning R, you could also try GMT (Generic Mapping Tools). It's essentially a command-line driven GIS. It has a wide variety of utilities including grdvolume which can "calculate volumes under a surface within specified contour" according to the manual.

I don't know how this software flew under my radar, but I wanted to thank you for pointing it out.  I think I can make great use of this.

---

