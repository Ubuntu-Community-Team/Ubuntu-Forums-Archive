---
title: "Gnuplot instant shutdown"
date: 2009-11-01
forum: Education &amp; Science
---

### Post by truth is life on 2009-11-01
I wrote an octave script to perform some calculations on a data set, and wanted to plot the results. However, when I put 'plot' commands in my script, the result was a gnuplot display opening and then instantly closing, before anything could happen or be seen. I've tried inserting commands to make the script hold there for a long time, like very long loops or user prompts, and I've looked at the octave manual, but I haven't been able to figure out how to successfully plot anything. Anyone here know how to? (I am using octave 3.2.2-2build1 via synaptic)

---

### Post by gesslein on 2009-11-01
I don't know about Octave, but the -persist shell command line option of gnuplot will keep the plot window open until you close it.  That looks like that is the problem.  Without the running "gnuplot -persist", the plot window closes as soon as gnuplot quits or does something else, causing the shutdown you are experiencing.

Regards,
George Gesslein II

---

### Post by truth is life on 2009-11-01
> **gesslein said:**
> I don't know about Octave, but the -persist shell command line option of gnuplot will keep the plot window open until you close it.  That looks like that is the problem.  Without the running "gnuplot -persist", the plot window closes as soon as gnuplot quits or does something else, causing the shutdown you are experiencing.

Regards,
George Gesslein II

Well, it turned out the problem was that the file I was *editing* to try to fix the problem was not the same as the file that was *actually being run*, since I was using the console history functionality, but had changed  the name in the middle. Whoops! :oops:

But now I'm getting a different, weirder error. I modified that same script so that it would put out the data into a .dat file, formatted  just the way gnuplot likes it. I try to plot it, and for some reason gnuplot inserts a datapoint which is not actually there in the upper right hand corner! Very bizzare. I checked the files, and they don't have a data point in that exact point

---

