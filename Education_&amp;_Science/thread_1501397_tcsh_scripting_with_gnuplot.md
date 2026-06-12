---
title: "tcsh scripting with gnuplot"
date: 2010-06-04
forum: Education &amp; Science
---

### Post by lordhaworth on 2010-06-04
Hi all,

I have ~1500 data files for which I want to produce graphs in gnuplot and save. I have been using gnuplot a while and know how to do this for individual files, but dont want to have to do it manually 1500 times!
From what I have seen you can loop in gnuplot scripts, but I am not convinced that this will help me plot and save all of my graphs. I think my best bet would be some tcsh script. I am a total novice, but was thinking something like:

for i in *; do
gnuplot
...
echo plot "$i"
...
exit
done

If anyone knows how to do this in gnuplot alone that would be great too, but my search so far has come up with nothing. 

Cheers

---

### Post by lordhaworth on 2010-06-04
May have solved this already:

[http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html](http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html)

---

