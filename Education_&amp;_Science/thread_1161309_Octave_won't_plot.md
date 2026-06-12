---
title: "Octave won't plot"
date: 2009-05-16
forum: Education &amp; Science
---

### Post by Johnco on 2009-05-16
Hi everyone. I just decided to have a clean install of Ubuntu 9.0.4 on my laptop.

i installed octave 3.0.1 from synaptic, which brought gnuplot among other dependencies. Everything installed just fine, but Octave won't plot.

A simple command such as:

```

octave:1> x=[0:0.1:1];
octave:2> plot(x,x,";something;");

```

will produce the given output:

```

error: `have_newer_gnuplot' undefined near line 1589 column 7
error: if: error evaluating conditional expression
error: evaluating if command near line 1589, column 3
error: called from `__go_draw_axes__:get_text_colorspec' in file `/usr/share/octave/3.0.1/m/plot/__go_draw_axes__.m'
error: evaluating assignment expression near line 90, column 17
error: evaluating if command near line 87, column 5
error: evaluating if command near line 25, column 3
error: called from `__go_draw_axes__' in file `/usr/share/octave/3.0.1/m/plot/__go_draw_axes__.m'
error: evaluating switch command near line 58, column 4
error: evaluating for command near line 56, column 2
error: evaluating if command near line 33, column 7
error: evaluating if command near line 26, column 5
error: evaluating if command near line 25, column 3
error: called from `__go_draw_figure__' in file `/usr/share/octave/3.0.1/m/plot/__go_draw_figure__.m'
error: evaluating if command near line 81, column 6
error: evaluating if command near line 78, column 4
error: evaluating if command near line 76, column 2
error: evaluating for command near line 75, column 7
error: evaluating if command near line 45, column 5
error: called from `drawnow' in file `/usr/share/octave/3.0.1/m/plot/drawnow.m'

```

any idea?

thanks in advance!

---

### Post by jpkotta on 2009-05-24
That variable is defined right in /usr/share/octave/3.0.1/m/plot/__go_draw_axes__.m.  Does your __go_draw_axes__.m have the following declaration?

```
    persistent have_newer_gnuplot ...
      = compare_versions (__gnuplot_version__ (), "4.0", ">");

```

Also, be sure that you have the gnuplot-x11 package installed.
```
dpkg -l gnuplot-x11
```
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnuplot-x11    4.2.4-6        A command-line driven interactive plotting p

```

---

### Post by Johnco on 2009-05-24
I have this in /usr/share/octave/3.0.1/m/plot/__go_draw_axes__.m

```
    persistent have_newer_gnuplot ...
      = compare_versions (__gnuplot_version__ (), "4.0", ">");
```

As for gnuplot-x11, it' is installed, a different version from yours, but installed.

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnuplot-x11    4.2.3-1        X11-terminal driver for gnuplot
```

---

### Post by jpkotta on 2009-05-26
> **Johnco said:**
> I have this in /usr/share/octave/3.0.1/m/plot/__go_draw_axes__.m

```
    persistent have_newer_gnuplot ...
      = compare_versions (__gnuplot_version__ (), "4.0", ">");
```

After I made my post, I looked more carefully at the file, and the declaration appears in several functions.  Make sure it's in the function where the error occurs (forunately there's a line number in the error).  

My bet is that it is there, which makes the error message very strange. 

Probably the best thing to do is ask the octave mailing list.  In the meantime, I would try hard coding it in there without the "persistent", e.g.
```
have_newer_gnuplot = 1
```

> **Johnco said:**
> 
As for gnuplot-x11, it' is installed, a different version from yours, but installed.


I forgot that I installed a newer version to fix mouse zooming.  But I have machines with the Ubuntu version installed and they work fine.

---

