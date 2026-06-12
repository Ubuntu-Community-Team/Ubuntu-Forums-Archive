---
title: "How to make a new path permanent in Octave"
date: 2012-12-04
forum: Education &amp; Science
---

### Post by afz12 on 2012-12-04
I am new to Octave and started learning it yesterday. I tried solving psuedoinverses and this worked well in a single file via the terminal commands

(y = A x => x = (A' A)^-1 A' y; where A can be rectangular). However I want to make a number of general task files as *.m.

I put the psuedoinverse algorithm in a text file (PI.m) and saved to Desktop/GP and found I needed to set a path so Octave could find it. After trolling through the Octave manual (no mean feet!) I found 

addpath("~Desktop\PI");

worked and I could run the algorithm as x = PI(A, y) and was quite surprised that I could have massive matrices A running quickly (m = 1,000000, n = 20) with excellent accuracy. I checked using "path" and all paths showed as well as this new addition. I closed Octave and repeated. However the path command showed the addition was only temporary! 

How can I make this new path permanent? I seems inconvenient to have to insert path detail at the start of each experimental file I want to play with?

Thanks in advance.

---

