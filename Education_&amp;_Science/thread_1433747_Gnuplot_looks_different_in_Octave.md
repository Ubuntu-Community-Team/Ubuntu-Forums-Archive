---
title: "Gnuplot looks different in Octave"
date: 2010-03-19
forum: Education &amp; Science
---

### Post by rob_l_f on 2010-03-19
Hi there,

I just wondered if someone might be able to help me with this; If I run Gnuplot from the command line and plot something, eg:

[ATTACH]150614[/ATTACH]

it looks quite nice.  But if I plot from Octave, it comes out like this:

[ATTACH]150615[/ATTACH]

Now I know I could probably mess around with it for hours to get it looking similar, but my question is, why does Gnuplot look so different through Octave?  Is there a way I can force it to use it's normal style?

Also I know I could just export the data and plot it in Gnuplot, but that's less convenient ;)

I'm using Octave 3.2 from the repos on Karmic

Many Thanks.

---

### Post by not_a_phd on 2010-03-19
Looks like your gnuplot comes up in the wxt terminal by default in the command line. To get this from octave, edit the .octaverc file in your home directory and add this line  

```
setenv("GNUTERM","wxt")
```


Direct your thanks to iwolf_fr from the thread: [http://ubuntuforums.org/showthread.php?t=1356561&highlight=octave](http://ubuntuforums.org/showthread.php?t=1356561&highlight=octave)

---

