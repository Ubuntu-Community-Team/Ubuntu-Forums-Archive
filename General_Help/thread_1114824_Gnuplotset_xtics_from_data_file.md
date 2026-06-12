---
title: "Gnuplot:set xtics from data file"
date: 2009-04-03
forum: General Help
---

### Post by dakebusi on 2009-04-03
Hi,

I'd like to have a plot in gnuplot with the tics being labeled with some data stored in the file I'm plotting.

I know how to do this using:

```
plot 'file.dat' using 2:xticlabels(1)
```

However, with this I only get the tic labels to be the data stored in the first column of the file. What I'd really like is to combine multiple columns to form the labels. Is that possible?

Thanks.

---

