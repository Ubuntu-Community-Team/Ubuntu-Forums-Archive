---
title: "(quite) specific R question about factors"
date: 2007-12-18
forum: Education &amp; Science
---

### Post by madmaxx on 2007-12-18
Hi there!
That's for all you R experts out there. I have a factor "hours" with several levels:

```

 Factor w/ 8 levels "h0","h10","h2",..: 7 7 4 3 7 5 3 7 3 4 ...
 h0 h10  h2 h20 h40 h41  h5 h99 
 94 432 726 263 132 117 610  61

```

I want the levels to be renamed and -- most importantly **reordered** (note the different order of the frequencies in the second example) -- so that I get something like this:

```

 Factor w/ 8 levels "0","2","5",..: 7 7 4 3 7 5 3 7 3 4 ...
   0   2   5   10  20   40   99  NA's 
  94 726 610 432  263  132  117  61 

```

How would I do that?
Thanks a lot, madmaxx

---

### Post by plvera on 2007-12-18
The following should work for reordering your variable. Just fill in your levels, I just typed in some random ones.

> hours=c(0,4,6,7,9,10)
> hours
[1]  0  4  6  7  9 10
> hours=factor(levels=c("0","4","6","7","9","10"))
> hours
factor(0)
Levels: 0 4 6 7 9 10

I hope this helps.

---

### Post by digisus on 2007-12-20
plvera,
sorry, I think I was not clear in my question. I already -have- a factor (not a vector) with levels defined. Let me try again.


This factor looks good EXCEPT that the order of the levels is not what I want. (Why? Because the numbers 0, 10, 2, etc. mean "0h", "up to 2h", "up to 5h", etc. So, there is a logical order and I want them to show (and plot!) in that order.

```

 Factor w/ 7 levels "0","10","2","20",..: 7 7 4 3 7 5 3 7 3 4 ...
   0   10    2   20   40   99    5 NA's 
  94  432  726  263  132  117  610   61 

```

How can I keep everything and only change this order? The goal is the factor to look like this:

```

 Factor w/ 7 levels "0","2","5","10",..: 7 7 4 3 7 5 3 7 3 4 ...
   0    2    5   10   20   40   99 NA's 
  94  726  610  432  263  132  117   61

```

I hope it is clearer now.
Thanks, digisus (aka madmaxx, my old login)

---

### Post by plvera on 2007-12-20
Hi madmaxx:

I often use "ordered"  to convert factors into ordered factors, for example:

> hours=c(0,2,5,7,9,11)
> hours=ordered(hours,levels=c("0","2","5","7","9","11"))
> levels(hours)
[1] "0"  "2"  "5"  "7"  "9"  "11"

You can type any text description(i.e. level=c("0h","2h"...). You should then be able to plot your factor and retain the order.

I hope this helps. If not, maybe trying the R-help list?

Regards

---

### Post by digisus on 2007-12-21
Hi plvera

Great, it works! Thanks a lot! :KS
And sorry, I simply did not get it the first time... :-\"

Merry Christmas,
digisus

---

