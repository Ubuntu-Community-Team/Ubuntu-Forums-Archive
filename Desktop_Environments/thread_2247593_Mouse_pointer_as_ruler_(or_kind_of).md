---
title: "Mouse pointer as ruler (or kind of)"
date: 2014-10-09
forum: Desktop Environments
---

### Post by mamboknave on 2014-10-09
[FONT=Courier New]
The mouse pointer is based on instantaneous coordinates of its position on the screen, say (X,Y).

On my desktop it displays as an arrow.

I need it to be displayed as the the intersection of the horizontal X and vertical Y lines all across the screen, top to bottom (X) and left to right (Y).

That means, when the mouse moves, the intersection of the two lines moves, carrying the lines with the movement.

Something like:

[INDENT] | [/INDENT]
[INDENT] | [/INDENT]
[INDENT] | [/INDENT]
-----+--------
[INDENT] | [/INDENT]
[INDENT] | [/INDENT]

Does anyone know of any package/tool that can make the mouse pointer looking like that?

I need it for Ubuntu 12.04.

Thanks!
[/FONT]

---

### Post by tgalati4 on 2014-10-09
There are a couple of packages:

tgalati4@Mint14-Extensa ~ $ apt-cache search ruler
texlive-latex-extra - TeX Live: LaTeX supplementary packages
distributed-net - donate unused CPU cycles - client for distributed.net
carmetal - dynamic geometry software with highly ergonomic UI
**kruler - screen ruler**
libgtkdatabox-0.9.1-1 - Gtk+ library to display large amounts of numerical data
libgtkdatabox-0.9.1-1-dev - Gtk+ library to display large amounts of numerical data
libgtkdatabox-0.9.1-1-glade - Gtk+ library to display large amounts of numerical data
libgtkdatabox-0.9.1-1-libglade - Gtk+ library to display large amounts of numerical data
screenlets - Widget-like mini-applications for GNOME
screenlets-doc - Widget-like mini-applications for GNOME - Documentation package
screenlets-pack-all - Widget-like mini-applications for GNOME
screenlets-pack-basic - Widget-like mini-applications for GNOME
**screenruler - measure objects on screen with a variety of metrics**
spek - acoustic spectrum analyser

There may be some scripts to perform a similar function.  What is the Use Case?  What exactly are you trying to measure?  Distance between stars in a digital picture? What units of measurement do you need?

---

### Post by mamboknave on 2014-10-09
@tgalati4
Thanks. I'm going to check it out asap.
>>  What is the Use Case
Gnuplot. When displaying multiplots, it issues static graphs, not interactive. Therefore, there is no way to see how data allign. That's done with X,Y lines on intercative graphs.
I need X & Y lines on the desktop to see how data allign on the different plots.

---

### Post by tgalati4 on 2014-10-09
It's been years since I've done serious data crunching with gnuplot.  I recall a mode where you could hover over a datapoint to see its values.  There is probably an open-source data plotter with that capability.

Let me google that for you:

[http://www.live-graph.org/](http://www.live-graph.org/)

[http://mesa.ac.nz/?page_id=2327](http://mesa.ac.nz/?page_id=2327)

[http://ptsg.berkeley.edu/~jhammel/plot.html](http://ptsg.berkeley.edu/~jhammel/plot.html)

---

