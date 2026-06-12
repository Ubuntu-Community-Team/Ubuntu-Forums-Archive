---
title: "3d plots (of scientific data), like GNUplot, but interactive"
date: 2009-05-05
forum: Education &amp; Science
---

### Post by Cracauer on 2009-05-05
I'm making charts like this in GNUplot:

[img]http://www.cons.org/tmp/time3d.png[/img]

I'm overall very happy with GNUplot for generating these things. Functionality and options are what I need.

But actually viewing this information is tough. While the GNUplot viewer allows you to turn and zoom this is by far not good enough to explore this data space.  First of all it's way too slow (thousands of datapoints and no hardware 3D OpenGL used) and second there is no way to point the mouse to a particular region and have it tell you what the data was.  I need to dive into one of these trenches that you see and have a look at what's going on.

Is there a way to do the same thing as GNUplot here, but view the 3D in a real 3D viewer?

I am thinking along the lines of exporting GNUplot data to Wings3d or Blender (doesn't exist, I checked) or an entirely different package.

Any opinions?

---

### Post by epitaph on 2009-05-05
Scilab supports 3 dimensional plots and viewing. It's possible in MATLAB too, though MATLAB is not free software. There are simple rotate and zoom tools to interact with the plots. Might be worth looking into. Perhaps someone will have a simpler suggestion.

---

### Post by sdbrogan on 2009-05-06
Ggobi might be useful to you :
[http://www.ggobi.org](http://www.ggobi.org)
It has a lot of cool features for high-dimensional data, including identifying a point when you move the mouse over it.  I'm not sure how fast it will be with large datasets, though.

---

### Post by WW on 2009-05-06
You could also check out [mayavi](http://code.enthought.com/projects/mayavi/) ([gallery](https://svn.enthought.com/enthought/wiki/Mayavi/Gallery)).

---

### Post by Cracauer on 2009-05-07
mayavi2 looks promising. I just hope they have full non-interactive capabilities, too.

---

### Post by Cracauer on 2009-05-07
> 
(python:31839): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
ERROR: In /build/buildd/vtk-5.0.3/IO/vtkPLOT3DReader.cxx, line 771
vtkPLOT3DReader (0x9f9c6b0): Encountered premature end-of-file while reading the geometry file (or the file is corrupt).

Segmentation fault


Oh well.

I wanted to do something with OpenScenegraph anyway, why don't I get off my lazy behind and get cracking on it?

---

