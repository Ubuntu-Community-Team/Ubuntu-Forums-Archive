---
title: "gnuplot multiplot"
date: 2013-05-03
forum: Education &amp; Science
---

### Post by Robin457 on 2013-05-03
Hello everyone,

im trying to create a special graphic with gnuplot and dont really get where i want.

What i want to do is this:
I have 20 textfiles containing 8000x2 matrices, where the first column  represents the time and the second the amplitude of a wave.
Now all 20 wave-functions shell be plotted in one graphic, that way that there is a vertical offset between them. 

The graphic should look like the one i attached to this post, where 60 functions a plotted above each other.

Does anybody now how to get there?


Thanks for reading ;)

---

### Post by tgalati4 on 2013-05-03
I would make a copy of all data files to a second directory, then write a script to add a Y field to the data with the correct offset.

I don't know how to do it in gnuplot directly, but I did find this:

[http://stackoverflow.com/questions/5786854/how-to-add-offset-to-data-from-file-while-plotting-in-gnuplot](http://stackoverflow.com/questions/5786854/how-to-add-offset-to-data-from-file-while-plotting-in-gnuplot)

It basically uses a math function to add the offset on the fly to the data.

---

### Post by steeldriver on 2013-05-03
I agree - a simple 2D plot with a suitably calculated offset

Have a look at this blog for how to do it directly in gnuplot --> [http://gnuplot-tricks.blogspot.ca/2010/01/plot-iterations-and-pseudo-files.html](http://gnuplot-tricks.blogspot.ca/2010/01/plot-iterations-and-pseudo-files.html)

For example, if I generate 21 files called sol-0, sol-1, ... , sol-20 then I can do:

```

gnuplot> unset key
gnuplot> set style data points
gnuplot> filename(n) = sprintf("sol-%d", n)
gnuplot> plot for [n=0:20] filename(n) using 1:(column(2) + n-20 + 10) linetype 1 pointtype 1

```
giving

[ATTACH=CONFIG]242139[/ATTACH]

---

