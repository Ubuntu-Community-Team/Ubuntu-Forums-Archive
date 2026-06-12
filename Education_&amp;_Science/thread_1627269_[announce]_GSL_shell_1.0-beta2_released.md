---
title: "[announce] GSL shell 1.0-beta2 released"
date: 2010-11-21
forum: Education &amp; Science
---

### Post by fr4nko on 2010-11-21
I'm glad to announce the release of [GSL Shell 1.0 beta2]("http://www.nongnu.org/gsl-shell/index.html"). This new release brings a lot of improvements in the graphics functions. Among the most remarkable new features you can now:

[LIST]
[*]put multiple plots on the same windows make animations
[*]have multiple graphical layers in a plot.
[/LIST]

The graphical rendering code was almost completely rewritten and optimised for to be efficient both for static plot and animations. You can find in the download directory also a window binary to try the program easily but on linux it is easy to compile the program by your self.

We have also a first implementation of a 3D plotting module based on the JavaScript Pre3d library of Dean Mc Namee. This module give you the possibility to create simple 3D plots and animations with a simple interface. Just be aware that, While this module is quite functional and usable, it could nevertheless replaced in future by a more efficient implementation. The reason is not the quality of the Pre3d code, which is excellent in itself, but the usage of JavaScript/Lua for 3D graphics which is inherently inefficient in term of speed and memory usage.

From the point of view of core mathematical functions we have also some interesting new features:

[LIST]
[*]new implementation of the interpolation functions with, notably, the Akima and cubic spline interpolation
[*]improvement of the handling of mixed operation between complex and real matrix
[/LIST]
There is also a new function to produce contour plot over a circular domain. The previous contour functions was only working on rectangular domains.

There is also a major change also the matrix operations sematic. Now GSL shell automatically promote a matrix to complex when the other operands are complex. This improvement includes the arithmetic operations, the matrix multiplications functions, and the matrix operations solve() and inv().

You can try the demo examples with the following commands:

> dofile('examples/pre3d.lua')
> demo1()

In the "examples" folder there are a lot of interesting examples.

I would appreciate any feedback, this is a beta release and is meant to fix some remaining bugs before the final 1.0 release.

Francesco

---

