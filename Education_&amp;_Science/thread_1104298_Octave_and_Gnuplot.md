---
title: "Octave and Gnuplot"
date: 2009-03-23
forum: Education &amp; Science
---

### Post by spacelem on 2009-03-23
Hi, I've run into a problem with Octave and Gnuplot.

Whenever I try to plot anything, even something as simple as
```
plot(1:10)
```
I just get a bunch of lines, one for each plotted point, saying:
```
gnuplot> 10 10 
         ^
         line 0: invalid command
```

Is there a way to fix this? I'm using Octave 3.0.1 and Gnuplot 4.2 patch 3, Should I try changing to a different version, of Gnuplot, and if so which one (and I haven't done any version fiddling in Ubuntu before, so I'm not sure how to do it!)

Thanks, Jamie

--
Erm, I think I may have posted this into the wrong category, sorry. Been a long day.

---

### Post by sudlex on 2009-03-23
try  this code  on octave 
x=1:0.1:180;
y=sin(x);
plot(x,y)

---

### Post by spacelem on 2009-03-23
> **sudlex said:**
> try  this code  on octave 
x=1:0.1:180;
y=sin(x);
plot(x,y)

Arcane magic. I have no idea why that worked, but it did.

I had a big dataset that I generated at work, and wanted to show someone at home. When I tried, I just got the rubbish I showed earlier, and then even x=1:10; plot(x,x); didn't work.

I had the same thing happen to me a while back at work, but I found that it was a really old version of gnuplot (from around 2005), and the problem went away only when I asked the sysadmin for a later version. As for why it happened today, I don't know, I wasn't doing anything obviously stupid.

Anyway, solved, until it breaks again.

---

