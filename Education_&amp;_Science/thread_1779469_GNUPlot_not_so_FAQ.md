---
title: "GNUPlot not so FAQ"
date: 2011-06-10
forum: Education &amp; Science
---

### Post by Paradigm6790 on 2011-06-10
Hello, I've exhausted my searches so I come humbly for help!

I have a graph that I am plotting information on, but the X-axis is not a uniform scale at start. The x I want goes as follows:

0.1 0.4 1 2 3 4 5 6 7 8 8 9 10 11 12 13 14 15 16 17 18 19 20

but I cannot figure out how to make the first two tics be a different scale.

Thanks!

---

### Post by Paradigm6790 on 2011-06-10
set xtics add (0.1) (0.4)

xD

This gets them on my graph, but I need them to be spaced as if they were on the same scale. Weird, I know, but that's how it needs to be done.

Here's a link to my current problem...
[IMG]http://i53.tinypic.com/2zfolxf.jpg[/IMG]

---

### Post by Johncy on 2011-06-11
Hi Paradigm6790,

> 0.1 0.4 1 2 3 4 5 6 7 8 8 9 10 11 12 13 14 15 16 17 18 19 20Looking at your x-axis data, you appear to have a conflict.  I believe, in order to make the 0.1 and 0.4 ticks to be on the same scale, the answer is to treat it as a bar graph and not as a line graph.  In this way, the x-axis data can be treated as a label with the "bars" equally spaced.  However, if you do this you will get two points labelled 8 and it appears from your example graph that you want them to appear as a single point.  If this is the case, then my suggestion will not work for you.

The attached graph was made in LibreOffice Calc to show the effect.  I hope this is of some help to you.

Best regards,

Johncy

---

