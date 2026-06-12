---
title: "3d scatter plot"
date: 2010-08-24
forum: Education &amp; Science
---

### Post by yotama9 on 2010-08-24
Hi guys. 

I'm searching for this for some time now and couldn't find this anywhere. 

Is there an open source  way, apart from VisIt which doesn't work on Ubunto,  to generate a 3d scatter plot on ubuntu? I have written a code which should produce something like this:
[IMG]http://www.chem.ucsb.edu/~browngroup/transparent_fluid_bilayer.png[/IMG]

And I can't show it. 

Thanks.

---

### Post by kurtjx on 2010-08-24
One option is to use Processing - [http://processing.org/](http://processing.org/)

It's rather easy to use Processing within a Java project if you're in Java land.  Alternatively you might just create a csv with your data, parse it all in Processing, and then visualize.

There's a python port too, but that did not work for me on Ubuntu...

Also, the Javascript port is pretty mature if you're doing web stuff.

---

### Post by Azrael3000 on 2010-08-24
Did you have a look at paraview yet? I think it should be capable of doing this sort of plot. (You might have to look into the pvmeshless toolbox)

---

### Post by yotama9 on 2010-08-24
ParaView looks good. I'm toying around with it.

Thanks

---

### Post by mdshaver on 2010-09-30
gnuplot 

[http://www.gnuplot.info/](http://www.gnuplot.info/)

[http://old.nabble.com/how-do-I-create-a-3d-scatter-plot.-td29496064.html](http://old.nabble.com/how-do-I-create-a-3d-scatter-plot.-td29496064.html)


The best way to learn gnuplot is the book below

[http://www.amazon.com/Gnuplot-Action-Understanding-Data-Graphs/dp/1933988398/ref=sr_1_1?s=gateway&ie=UTF8&qid=1285905423&sr=8-1](http://www.amazon.com/Gnuplot-Action-Understanding-Data-Graphs/dp/1933988398/ref=sr_1_1?s=gateway&ie=UTF8&qid=1285905423&sr=8-1)

---

### Post by Azrael3000 on 2010-10-01
well for such a scatter plot as in the forum thread you described it might be indeed better to use gnuplot. For the task the op is looking for I'd rather use paraview since it does have a lot more features (filters + pvmeshless plugin) and is also much more intuitive to use than gnuplot.

---

### Post by earlycj5 on 2010-10-01
I've used the RGL package in R before to do similar work.

[http://rgl.neoscientists.org/about.shtml](http://rgl.neoscientists.org/about.shtml)

There's other packages in R that will do this as well.

---

### Post by earlycj5 on 2010-10-01
And another for making 3D scatterplots in R using R-Commander
[http://decisionstats.wordpress.com/2010/09/30/creating-3d-graphs-with-data-in-r/](http://decisionstats.wordpress.com/2010/09/30/creating-3d-graphs-with-data-in-r/)

---

### Post by radioboy on 2010-10-08
Also check VTK, MayaVi and OpenDX:
[http://www.vtk.org/]("http://www.vtk.org/") 
[http://mayavi.sourceforge.net/index.html]("http://mayavi.sourceforge.net/index.html")
[http://www.research.ibm.com/dx/]("http://www.research.ibm.com/dx/").

---

