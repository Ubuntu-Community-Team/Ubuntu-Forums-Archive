---
title: "connecting point with gnuplot"
date: 2009-06-26
forum: Education &amp; Science
---

### Post by Benzaa on 2009-06-26
I need some help for gnuplot.

I want to connect some points, but, the input data has a blank line between data. It looks something like this:

x  t
0  200

1  300

2  400

3  500

With this format, I can only plot points.

Any ideas of how to connect the points??
And I cannot change the format, that would mean to change a lot of files.

---

### Post by xadder on 2009-06-30
I would run a script to remove the blank lines from all the input files, e.g.

```

for i in oldfiles.*
do
  awk '{if(NF>0) print $0}'   $i > new.$i
done

```

Or if you prefer perl, use 

```

for i in oldfiles.*
do
  perl -ne '{print unless /^\s+$/}'  $i > new.$i
done

```

The awk code is printing lines where the number of fields (NF) > 0. The perl script prints when there is either nothing or some white space characters (\s) between the start (^) and end ($) of the line.

---

### Post by Benzaa on 2009-06-30
Thanks for the idea

I will use awk.

---

