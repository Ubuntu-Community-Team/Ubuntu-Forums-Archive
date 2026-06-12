---
title: "gnuplot slowing down machine?"
date: 2009-04-16
forum: Education &amp; Science
---

### Post by GTengineer on 2009-04-16
Hello all,

I recently started using gnuplot (ver 4.2 patchlevel 4) but whenever I launch a plot, it brings my computer to a crawl. I am running it in an Kubuntu 9.04 virtualbox.

Here is the batch line command I am issuing:
> echo -e "set xlabel \"x\"\nset ylabel \"y\"\nset title \"My Plot\"\nplot 'history.dat' using 3 with lines" > input.txt | gnuplot -persist input.txt

After looking with top, I see gnuplot is almost always using around 50% CPU resources, and I also see a so called "polkit-read-aut" which drops in and out consuming as much as 60% CPU resources. 

Has anyone experienced something similar to this?
Thanks

P.S. It only occurs when I run in batch mode with the -persist flag

---

