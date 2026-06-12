---
title: "gnuplot question"
date: 2009-04-02
forum: General Help
---

### Post by vandinsh on 2009-04-02
gnuplot
set title 'Nosaukums' 
set xlabel 'Baiti' 
set ylabel 'Laiks' 
set format y "%.0f"
set xrange[0:8388608]
set yrange[0:713181520]
plot 'test' with lines
exit

I would like to see real numbers ( not rounded ) on the x, y axis. How can I change my script? Please help! :)
Thanks!!!

---

### Post by jigsaws on 2009-04-02
So why do you use %.0f ?

---

### Post by vandinsh on 2009-04-02
Because without it, I get numbers like 1+e7...What can you advise me please?

---

