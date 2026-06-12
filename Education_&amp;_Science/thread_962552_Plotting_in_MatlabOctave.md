---
title: "Plotting in Matlab/Octave"
date: 2008-10-29
forum: Education &amp; Science
---

### Post by in_flu_ence on 2008-10-29
I have an iteration, say, an increasing array. How can I plot the data point and see it while it is running the iteration? Meaning I can see that a new data point is added as a iternation commences.

x=0;
y=0;
ar=[];

while (x<1000000)
    ar=[ar;x,y]
    figure(1),plot(ar)
    x=x+1;
    y=y+2;
end

Many thanks

---

### Post by normandin on 2008-10-31
you might try something like this:

```

x = 0;
y = 0;
ar = [];
figure;
hold on;
while (x < 100)
  ar = [ar; x; y];
  plot (ar);
  drawnow;
  x = x + 1;
  y = y + 2;
end;

```

i'd advise keeping the limit on your while loop well under a million, the repeated plotting is a resource hog.  for a reference, the value of 100 that i used took about 30 seconds to run.

---

### Post by in_flu_ence on 2008-11-04
Thanks very much. It works.

---

