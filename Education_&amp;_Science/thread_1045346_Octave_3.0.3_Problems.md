---
title: "Octave 3.0.3 Problems"
date: 2009-01-20
forum: Education &amp; Science
---

### Post by kidcharles on 2009-01-20
Hi all, I just installed the octave3.0 package on my fresh 8.04.1 installation and it is pretty bugged. I put in a simple script and it executed it in a continuous loop for no apparent reason.

```

data = load "011909a.txt";
v = data(:,3);
d2 = data(:,4);

figure
plot(v,d2)

```

Also, the 'plot' command does not work. I tried to compile the latest octave from source but I had a compilation error. Anyone else having these problems? Is there an alternate package out there, even an older one, that would work better? Thanks.

---

### Post by kidcharles on 2009-01-20
Haha, Octave is fine, I just did something hilariously stupid. I named my script plot.m. I guess that will teach me.

---

