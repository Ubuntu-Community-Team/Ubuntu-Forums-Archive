---
title: "transform colon data to vector view. possible?"
date: 2009-10-22
forum: Education &amp; Science
---

### Post by awayguy on 2009-10-22
Halo

so my problem is the following:

iv got a big list of the following data:


  x    y
  0.0 20.30011
  1.0 20.31087
  2.0 20.31229
  3.0 20.31206
  4.0 20.31387
  5.0 20.31541
  6.0 20.32034
  7.0 20.32324
  8.0 20.32302
  9.0 20.32924
 10.0 20.33236
 11.0 20.33089
 12.0 20.33640
 13.0 20.33448
 14.0 20.33371
 15.0 20.33557
.
.
.
.

now i want to split the x column from the y column. afterwards i want transform the x and the y column to a vector form:

it should look like this:

x: (0.0, 1.0, 2.0, 3.0, 4.0.......)
y: (20.30011, 20.31087, 20.31229......)


so is this possible to do it in a very simple way, or do i have rewrite each data by Backspace and enter etc etc etc.....

would be glad if someone could help

---

### Post by ahmatti on 2009-10-22
One option is to do it R, suppose that your data is in file list.txt:

```

#Read in data
data <- read.table('list.txt')
#transpose the data
tdata <- t(data)
#View the data
tdata

```

Or you could do it using awk (from [http://www.commandlinefu.com/commands/view/1427/transpose-a-file):](http://www.commandlinefu.com/commands/view/1427/transpose-a-file):)
```

awk '{ for (f = 1; f <= NF; f++) a[NR, f] = $f } NF > nf { nf = NF } END { for (f = 1; f <= nf; f++) for (r = 1; r <= NR; r++) printf a[r, f] (r==NR ? RS : FS) }' list.txt
```

---

