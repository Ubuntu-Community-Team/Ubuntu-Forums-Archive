---
title: "Charts/trees in Latex?"
date: 2009-02-25
forum: Education &amp; Science
---

### Post by urukrama on 2009-02-25
How would I draw charts in Latex? I want to draw some basic tree-type charts (like in family tables), but wouldn't know how to do so or what package to use.

---

### Post by hubie on 2009-02-25
The usual drawing suspects would probably do the job, such as [OpenOffice Draw]("http://www.openoffice.org/product/draw.html"), [Kivio]("http://www.koffice.org/kivio/"), [Dia]("http://projects.gnome.org/dia/"), [xfig]("http://www.xfig.org/"), and [Inkscape]("http://www.inkscape.org/").  You'd probably want a vector-based drawing program, so you can search [Freshmeat]("http://freshmeat.net/") to turn up others as well.

If you are doing family trees, you can go hardcore and dive into [GRAMPS]("http://www.gramps-project.org/wiki/index.php?title=Main_Page"), and from that you can spit out a family tree as well.

The trick then becomes converting whatever those output to eps files for latex (or png files for pdflatex).  Your handy [convert]("http://amath.colorado.edu/computing/software/man/convert.html") command can do wonders, which you get if you install [ImageMagick]("http://www.imagemagick.org/script/index.php").  I've also used Gimp to convert images.

Probably the best way, but one that I have never used so I cannot personally recommend, is using [Asymptote]("http://asymptote.sourceforge.net/"). It is based on Metapost, so it is TeX/LaTeX friendly.  A quick scan of the web page looks like that if you know how to do latex (without using a latex editor), then you can probably get up to speed pretty quickly.

Having said/written all that above, I stumbled upon [this page]("http://www.essex.ac.uk/linguistics/clmt/latex4ling/trees/") that tells you a variety of ways to do trees in latex.  You might also find [this site]("http://wiki.loria.fr/wiki/Drawing_LaTeX_trees"), or maybe [this site]("http://mally.stanford.edu/~sr/computing/latex-example.html") useful.

---

### Post by eljalill on 2009-02-26
For all such drawings and graphs I usually use metapost, I find it nicely compatible with Latex, and I find it pretty powerful.
However, it does take some time to learn how to use it correctly...
metapost is (who would have thought) in the texlive-metapost package.

---

### Post by hugmenot on 2009-02-26
Tikz/PGF package:

[http://www.texample.net/tikz/examples/feature/trees/](http://www.texample.net/tikz/examples/feature/trees/)

It&#8217;s a pure Latex solution.

---

### Post by dikarus on 2009-02-28
GLE is a very hand tool for trees and charts and it's very easy to use:
[http://glx.sourceforge.net/]("http://glx.sourceforge.net/")

go to the examples -> diagrams section and you'll see how easy it is!

---

### Post by knattlhuber on 2009-10-16
There is also GraphViz, an extremely handy tool for drawing flow charts:
[http://graphviz.org/]("http://graphviz.org/")

---

### Post by Arpad Horvath, Szfvar on 2012-11-20
> **hugmenot said:**
> Tikz/PGF package:

[http://www.texample.net/tikz/examples/feature/trees/](http://www.texample.net/tikz/examples/feature/trees/)

It&#8217;s a pure Latex solution.

For LaTeX I recommend TikZ too. It is very nice and powerful.

---

### Post by howefield on 2012-11-20
Old thread back to sleep.

---

