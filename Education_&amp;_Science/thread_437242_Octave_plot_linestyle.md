---
title: "Octave plot linestyle"
date: 2007-05-08
forum: Education &amp; Science
---

### Post by tkjacobsen on 2007-05-08
Does anyone know how a make a dashed / dotted / dash-dotted line in octave.

(Currently using octave-2.9.9 from fristy repos)

---

### Post by sam81 on 2007-05-08
good question, just tried thinking it was the same as matlab but it isn't. It works like matlab however if you get
octplot. Install it and then to use it call 
```
 octave> toggle_octplot
```
it works with the 2.1 branch, haven't tried with the 2.9 branch but I think it should work

---

### Post by ahmatti on 2007-05-09
Use plot(x,y,'.'), or plot(y,'.') type help plot in octave to see all of the linestyles.

---

### Post by tkjacobsen on 2007-05-09
> **ahmatti said:**
> Use plot(x,y,'.'), or plot(y,'.') type help plot in octave to see all of the linestyles.

help plot doesn't say anythong about linestyles... 
'.' is just plotting all the points as dots, this is not what i'm looking for.

BTW:
Octplot does it fine, but i don't think the plots are pretty. Maybe it is possible to use matplotlib in octave?

---

### Post by ahmatti on 2007-05-09
Maybe you need to have some of the octave docs package installed for the help to work? As far as I know matplotlib doesn't work in Octave - and I am pretty sure I'm right ..

Here is what I get for line styles with help plot:

  `-'
          Set lines plot style (default).

    `.'
          Set dots plot style.

    `@'
          Set points plot style.

    `-@'
          Set linespoints plot style.

    `^'
          Set impulses plot style.

    `L'
          Set steps plot style.

and

    `+'
    `*'
    `o'
    `x'
          Used in combination with the points or linespoints styles,
          set the point style.

---

### Post by kakila on 2010-08-07
Maybe you want to read this
[http://savannah.gnu.org/bugs/?30545](http://savannah.gnu.org/bugs/?30545)

The problem is with gnuplot

JPi

---

### Post by PGScooter on 2010-08-08
Probably not what you're looking for, but if you are willing to spend some time getting to learn it, ggplot2 in R is extremely flexible, powerful, and intuitive.

---

### Post by kakila on 2010-08-08
I've never used R, though read about it.
Another option is to use scipy in python. Basically numpy + matplotlib, they present an interface very similar to octave/matlab.
Hopefully in the next release of Octave (coming very soon) they will extend the functionality of the "fltk" backend for plotting and "all" the problems will be solved.
You can experiment with the fltk backed.
Run 
> backend fltk

and then do your plots (you have all the line styles, control over the face color of the markers, mouse zoom, etc...)
You can also change the display of a given figure by
> backend(figure_handle, 'fltk')

JPi

---

