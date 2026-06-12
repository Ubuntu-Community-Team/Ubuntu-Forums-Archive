---
title: "best tool for programatic drawing of lines, arcs, points?"
date: 2008-01-02
forum: Education &amp; Science
---

### Post by christian.convey on 2008-01-02
Can anyone recommend a tool / library for this?

I've got a Python program whose output is a set of lines, arcs, and points.  I'm looking for a library, set of programs, etc. that will let me:

1) Display all of these objects on the screen, and
2) Let me pan and zoom.

Some of the objects are much bigger than a 1:1 pixel mapping allows.  (x = 0 ... 10,000, y = 0 ... 4000), but I also need to zoom in and carefully inspect some critical areas in close detail (something closers to 1:1 ration of my units to screen pixels).

I only have about 100 entities to draw, and the tool doesn't need to draw them in realtime.  For example, it would be OK for this to produce a PDF as long as I have some means of panning / zooming around a PDF.

BTW, this is all 2D, and I care much more about getting this done quickly than I do about polished output.  This is all so that I can visualize how a certain algorithm is working, to help me debug it.

Any ideas?

Thanks,
Christian

---

### Post by ssam on 2008-01-02
the svg format is pretty simple. either have a look at the spec, or make some simple files with inkscape.

you could then use inkscape to look at the results.

have a look at [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/325823](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/325823) (you will need to add an arc class)

next easiest might be cairo.

---

### Post by christian.convey on 2008-01-04
> **ssam said:**
> the svg format is pretty simple. either have a look at the spec, or make some simple files with inkscape.

you could then use inkscape to look at the results.

have a look at [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/325823](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/325823) (you will need to add an arc class)



Thanks, that's just what I'm looking for!

---

