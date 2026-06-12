---
title: "Accuracy in Octave"
date: 2009-03-05
forum: Education &amp; Science
---

### Post by mrwilly on 2009-03-05
Hi.

I'm using Octave to calculate a/(a-b) where a and b are real valued double-precision numbers.

I know that the output will not be perfect, but what I want to do is ensure that the output is always on one side of the true result.

For example, if a=1 and b=-2 then a/(a-b)=1/3 which cannot be represented perfectly in octave. What I want is for Octave to always give me output higher than the correct output in these situations, not less than.

So in this example, Octave might return 0.33333333333 which would be a tiny amount less than the true answer, but I'd like the output to be a tiny amount higher than the true answer (so 0.3333333333334 or something).

Is there some way to force Octave to estimate to one side? Or do I need to manually check the output each time?

Thanks

---

### Post by Xnst on 2009-03-05
I guess you just need the output rounded up to desired accuracy. One you decided how many decimals you want rounded upwards you can use ceil.

Example: You want r with 10 decimal accuracy:

```


>: ceil(r*1.e10)/1.e10


```

should give just that.

---

### Post by jpkotta on 2009-03-07
[http://en.wikipedia.org/wiki/Floating_point#Rounding_modes](http://en.wikipedia.org/wiki/Floating_point#Rounding_modes)

I have no idea how to actually change the mode, or how hard it would be to make octave use a different mode.

---

