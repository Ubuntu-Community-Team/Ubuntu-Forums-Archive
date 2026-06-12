---
title: "Command-line tool for plotting image data: ImageMagick?"
date: 2009-12-31
forum: Education &amp; Science
---

### Post by valavanisalex on 2009-12-31
Hi everyone,

I'm developing a new imaging system, which outputs data in three columns, containing the (x,y) coordinates and the "brightness" of each point in the image:

# X  Y    power
...  ...  ...
...  ...  ...

At the moment, I read the data into octave, reshape the third column into a matrix and make a pseudocolour plot, which I then export as a greyscale PNG image.

What I'd really like is a simple command-line method of directly converting the three-column data to a PNG image.  

I thought maybe ImageMagick would be capable of doing the job.  Has anyone had a good experience with it?  Any other suggestions?

Thanks!

---

### Post by HydrologyGuy on 2010-01-02
You could try Ploticus: [http://ploticus.sourceforge.net/doc/welcome.html](http://ploticus.sourceforge.net/doc/welcome.html)

It's very flexible for plotting, and it will output to PNG files.

---

### Post by PGScooter on 2010-01-02
How about gnuplot?

---

### Post by valavanisalex on 2010-01-03
Thanks guys!

I've tried using pm3d plots in gnuplot and it does roughly what I want.  However, it seems to require the data to be split into sets with a linebreak between each X value.  

Ploticus looks very promising: the heatmaps look ideal ([http://ploticus.sourceforge.net/gallery/gall.heatmap.html](http://ploticus.sourceforge.net/gallery/gall.heatmap.html))  I'll hopefully try it out when I'm back in the lab tomorrow and let you know how I get on.

---

### Post by valavanisalex on 2010-01-05
Thanks for the suggestions, it's actually very easy to do this in Gnuplot using the "image" 2D plot style.  You simply use

```
plot 'data.dat' with image
```

I've marked this thread as solved :)

---

### Post by barnex on 2010-01-11
> **djsik said:**
> Thanks for the suggestions, it's actually very easy to do this in Gnuplot using the "image" 2D plot style.  You simply use

```
plot 'data.dat' with image
```

I've marked this thread as solved :)

Handy, I'll remember that one, thanks.

---

