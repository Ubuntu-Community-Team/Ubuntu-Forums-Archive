---
title: "plotting with mixed logarithmic/linear scales"
date: 2007-03-27
forum: Education &amp; Science
---

### Post by jeremytaylor on 2007-03-27
Hi there, 
I am trying to make a plot like this 
[URL="http://lambda.gsfc.nasa.gov/product/map/current/map_images/PowerSpectrum1024.png"]http://lambda.gsfc.nasa.gov/product/map/current/map_images/PowerSpectrum1024.png
[/URL]
but am struggling to find a way of plotting an axis that changes from logarithmic to linear along its scale. 

In IDL I can fudge something by overlaying two plots. But I can't figure out a similar fudge for pylab.

Any ideas?

thanks
Jeremy

---

### Post by Steveire on 2007-03-27
Look into this: [http://matplotlib.sourceforge.net/matplotlib.pylab.html#-subplot](http://matplotlib.sourceforge.net/matplotlib.pylab.html#-subplot)

You might be able to create subplots, remove axes etc, and move the plots closer together. I haven't had much sucess  because the axes seem to be tight to the data no matter what I try.

---

### Post by NikoC on 2007-03-28
I have RLplot (available via the repos) installed on my system, I haven't been using it so far, but after a quick test you can transform your X-axis to a logaritmic one with one click... still have to figure out on how to export the chart though ;-)

---

### Post by Steveire on 2007-03-28
Have a closer look at the example he linked to.

It is not one simple logarithmic scale he needs. The axis changes scale after 100.

---

### Post by jeremytaylor on 2007-03-28
Thanks for the advice. Finally managed this (kindof) with careful use of axes() commands with matplotlib. 

My code is a mess so I won't stick it up here for you to laugh at but I'm happy to send it to interested individuals who come across this thread while trying to do the same thing.

thanks again
Jeremy

---

### Post by jeremytaylor on 2007-03-28
Okay, I just made  a simple example. You can see it's not perfect as there is a small gap between the lines... you can kindof fix this by fiddling the ranges but it's a bit tricky.

Any suggestions to get it looking right?

```

from pylab import *


t = arange(1.0, 1000.0)
y = sin(0.03*t)



#creates a frame with background
allaxes = axes([0.1, 0.1, 0.8, 0.8])
allaxes.xaxis.set_visible(False)
allaxes.yaxis.set_visible(False)

#this is the logarithmic bit
logbit = axes([0.1, 0.1, 0.4, 0.8],frameon=False)
logbit.yaxis.set_visible(False)


semilogx(t[0:199], y[0:199])
ax1=axis([1.0, 199.0, -1.5, 1.5])



#this is the linear bit
linbit = axes([0.5, 0.1, 0.4, 0.8], frameon=False)
linbit.yaxis.set_visible(False)

plot(t[200:], y[200:])
axis([200.0, 1000.0, -1.5, 1.5])

#this plots the y axis 
justxaxes = axes([0.1, 0.1, 0.8, 0.8], frameon=False, sharey=linbit)
justxaxes.xaxis.set_major_locator(NullLocator())


show()

```

---

