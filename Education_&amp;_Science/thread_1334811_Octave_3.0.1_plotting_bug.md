---
title: "Octave 3.0.1 plotting bug?"
date: 2009-11-22
forum: Education &amp; Science
---

### Post by PC_load_letter on 2009-11-22
I'm using the 32bit Octave version 3.0.1 from the Jaunty repos. I entered the following very simple instructions to plot y=sin(x) either in the terminal or via QtOctave, same result.

```
x=0:0.01:pi;
plot(sin(x))
```

The problem is the scaling of the X-axis, the plot itself is fine, but the range on the X as shown by the tick marks goes from 0 to more than 300 (0, 100, 200, 300), instead of just 1, 2, 3...etc. I checked gnuplot, but it's fine, it doesn't have this problem.

Can someone confirm this? Is this a known bug? 

Thanks.

---

### Post by Xnst on 2009-11-23
The x-axis in your case is the position in the vector sin(x). I guess you would like to use:

```
plot(x,sin(x))
```

instead.

---

### Post by PC_load_letter on 2009-11-23
Thanks, my mistake then.

---

