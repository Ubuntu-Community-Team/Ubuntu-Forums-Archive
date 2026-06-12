---
title: "errors with gnuplot and octave"
date: 2008-07-28
forum: Education &amp; Science
---

### Post by arkara on 2008-07-28
I have installed both gnuplot and octave.
but i get errors, when i try to give gnuplot commands in octave.
anyone knows anything?
=================================EDIT===================================
Ok let me Make it more clrear..
I have installed both gnuplot and octave, but the problem now is when i isue gnuplot commands on octave..
i get the following errors... like..
```
octave:15> gset term wxt
parse error:

  syntax error

>>> gset term wxt
             ^

```

---

### Post by thisismalhotra on 2008-07-29
Why are you tryin to issue GNUPLOT commands in  octave?
If I am correct octave does not work like GNUPLOT is just parses data to gnuplot to enable graphing capabilities. Most of this work is done by octave graphing function like plot3d on the backend.

Could you please elborate more on what is your issue exactly?

---

### Post by arkara on 2008-07-29
> **thisismalhotra said:**
> Why are you tryin to issue GNUPLOT commands in  octave?
If I am correct octave does not work like GNUPLOT is just parses data to gnuplot to enable graphing capabilities. Most of this work is done by octave graphing function like plot3d on the backend.

Could you please elborate more on what is your issue exactly?

When i plot something on octave..
i get a x11 output, i want to switch the output to wxt but i cant do it.
look for example...
[IMG]http://img362.imageshack.us/img362/7021/plotsjq5.png[/IMG]

the left image is from octave and the right image is from gnuplot..
do not see the line, but see how better(truetype) are the axis on the gnuplot...

---

### Post by Berto88 on 2008-07-29
if you save the plot as a postscript this usually plots a nicer line

print("filename.ps")

---

### Post by arkara on 2008-07-29
The thing is that in other sites, i have seen gnuplot commands used through octave, but when o try it i can't seem to do it.

---

### Post by Berto88 on 2008-07-30
I think octave have removed most of the gnuplot commands for the new version

version 3-0.1

what version are you running?

---

### Post by arkara on 2008-07-30
3-0.1
====EDIT====
sorry
it's 3-0.0

---

### Post by Berto88 on 2008-07-30
Looking around on the net, it seems gset command was removed for version 3 and above.

---

### Post by Berto88 on 2008-07-30
Looking around on the net, it seems gset command was removed for version 3 and above.

I used to be able to gset term postscript,

now i just use print("filename.ps")

try ```
help print
```

to see what different file output you can plot as and see if they improve the plot

---

