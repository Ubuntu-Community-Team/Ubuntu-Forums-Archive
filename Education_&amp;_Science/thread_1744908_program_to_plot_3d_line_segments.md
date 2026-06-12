---
title: "program to plot 3d line segments"
date: 2011-04-30
forum: Education &amp; Science
---

### Post by thisisbasil on 2011-04-30
hello all, i have done some research and haven't really found anything of note. does anyone know of any programs out there that allow me to plot line segments in 3d?

---

### Post by Azrael3000 on 2011-05-01
If you mean simply  a line between two points then you can use the vtk data format. The specification can be found here: [http://www.vtk.org/VTK/img/file-formats.pdf](http://www.vtk.org/VTK/img/file-formats.pdf)
There you'll also see some specific examples that illustrate the capability. Visualizing is then done in ParaView.

Another low-level option is always gnuplot.

If you have more questions feel free to ask.

---

### Post by thisisbasil on 2011-05-01
thanks!

paraview is nice. any idea of how to draw multiple lines at the same time? or is that in the vtk file you linked to?

---

### Post by tommpogg on 2011-09-06
I can suggest Octave or a combination LateX + Tikz library. Beware that both of them are quite hard to learn. But if you already know them, drawing a line in a 3D space should be straightforward.

---

