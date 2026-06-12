---
title: "how to enable octaviz?"
date: 2007-03-03
forum: Education &amp; Science
---

### Post by damian.rohraff on 2007-03-03
It is good there is no more broken dependencies between octave and octaviz (in feisty) :). Does anyone how to turn off gnuplot and activate octaviz?
Thanks
Damian

---

### Post by ahmatti on 2007-03-21
You don't need to separately enable octaviz and disable gnuplot. After installation you just call the desired octaviz plotting function from octave.

e.g plot(x,y) plots the graph in gnuplot but **vtk_plot(x,y) uses octaviz.**

---

### Post by juve on 2007-04-03
Tip for Edgy:
to install octaviz in edgy you have to install the virtual package **libvtk4c2a** from dapper.

---

