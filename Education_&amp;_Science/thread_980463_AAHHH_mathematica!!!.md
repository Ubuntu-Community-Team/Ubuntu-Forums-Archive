---
title: "AAHHH mathematica!!!"
date: 2008-11-12
forum: Education &amp; Science
---

### Post by rajan on 2008-11-12
i'm completely stuck on this mathematica problem...

i'm issuing the following command, where kappa has already been defined as 1.04 x 10^8:
Plot[150*E^(-kappa*x), {x, 0, 2*10^-9}]

and the graph goes below zero! AAAAAHHHH!!! i have been looking at this for so long that i think i see God. 

can anyone please tell me what i'm doing wrong? 

My first line of input was:
[CODE]
kb = 1.38*10^-23
T = 298
el = 1.6*10^-19
kappa = 1.04*10^8
taoO = (.9149 + .8765)/2[\CODE]

thanks for looking. i need any help i can get.

---

### Post by Proton Soup on 2008-11-13
looks like it's somewhere below 125, not below 0

---

### Post by rajan on 2008-11-13
ooooooooo i'm embarassed... i never would have looked for mathematica to put the x axis at somewhere other than y = 0. thanks a lot Proton Soup.

---

### Post by Proton Soup on 2008-11-13
we all get blind spots.  i didn't notice it at first, either.

---

