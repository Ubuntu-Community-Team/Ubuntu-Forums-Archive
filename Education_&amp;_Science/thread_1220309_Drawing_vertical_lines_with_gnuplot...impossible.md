---
title: "Drawing vertical lines with gnuplot...impossible?"
date: 2009-07-22
forum: Education &amp; Science
---

### Post by BetterSense on 2009-07-22
I simply want to draw a vertical line through an existing x/y plot at a specific point.

Plotting a horizontal line is easy....make the curve, then plop a line on it 

```
plot sin(x)
f(x)=$whateverconstant
replot f(x)
```

This draws the horizontal line through the graph wherever you want. I can't do the same thing with a vertical line, though. The only way I know how to draw a vertical line is parametrically. It's no good however

```

plot sin(x)
set parametric
replot $whateverconstant, t
undefined variable: x

```

this does not work. gnuplot says there is an undefined variable. I can't switch to parametric mode and replot. There must be a way to do this with gnuplot. All I want the lines for is basically for visual gridlines to highlight a certain X-coordinate on the graph.

---

### Post by PandaGoat on 2009-07-22
To plot a vertical line, you must plot it as a parametric function which you have already figured out.

What you want to do is use the multiplot feature of gnuplot.

Here is an example of multiplot:
```

set multiplot
plot sin(x)
set parametric
plot $whateverconstant, t with lines linecolor 2

```
The 'argument' "with lines linecolor 2" sets the line color to green.  It may seem confusing, but its a conglomeration of various options: "plot with . . .", "plot with lines [options for lines]", "plot with lines linecolor [a number representing a color]".

Happy plotting!

---

