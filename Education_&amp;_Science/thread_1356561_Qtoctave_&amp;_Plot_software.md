---
title: "Qtoctave &amp; Plot software"
date: 2009-12-16
forum: Education &amp; Science
---

### Post by iwolf_gr on 2009-12-16
Hello to all,
I am using QtOctave and Octave 3.0. I have tested octplot, oplot, yapso and easyplot. Unfortunately I was not satisfied from octplot and oplot.The yapso is pretty nice but if i drag the window, the image become transparent. The easy_plot returns errors   p, li { white-space: pre-wrap; }  [COLOR=#ff0000]QColor::setNamedColor: Unknown color name 'rgb(  0, 255,   0)'[/COLOR]

So i am stacked with gnuplot. I have edited the .octaverc and added this line  
setenv("GNUTERM","wxt")
So the GNUplot uses the widget window.

Any other suggestions???

---

### Post by not_a_phd on 2010-01-08
No. But, thanks for your suggestion. I must say that I do like gnuplot in its stand alone mode, but do not care for the default font and grid styles in the octave interface.

---

