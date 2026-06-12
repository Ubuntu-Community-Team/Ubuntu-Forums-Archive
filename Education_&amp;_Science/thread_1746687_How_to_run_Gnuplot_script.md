---
title: "How to run Gnuplot script"
date: 2011-05-02
forum: Education &amp; Science
---

### Post by Senplanet on 2011-05-02
Hello
I am trying to run my simple gnuplot script for csv input file directly from terminal.
The content of my script "test.gp" is:
```

set datafile separator ","
set autoscale
plot "Nye.csv" using 2 every ::1 with linespoints linestyle 7

```

I run the script by typing: gnuplot test.gp
I got the window with desired plot but its immediately closed.
I don't know whether the command is wrong or I miss something in the script. However, if I copy line by line to gnuplot terminal, it works... Anybody has experience with running gnuplot script on ubuntu?

---

### Post by Lateralis on 2011-05-03
The script looks OK, but if you run a script from the command line you need to tell gnuplot to pause

```

pause -1

```

This forces gnuplot to wait for you to close the window.  Without it the script will execute quite happily but leave nothing for you to view.  

Alternatively, you can tell gnuplot to print the plot to file, which you can open up and view yourself, e.g.

```

#!/usr/bin/gnuplot
plot '<SOME FILE>' using 1:2  w lines, '<SOME LEGEND>' 
set terminal postscript portrait enhanced mono dashed lw 1 'Helvetica' 14
set output '<SOME OUTPUT FILE>.ps'

```

You can then use some viewer, such as evince in Gnome to view the graph.  Or change the file extension and terminal from postscript to save the graph in some other (raster) format.

---

