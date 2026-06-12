---
title: "[SOLVED] gProms kernel error"
date: 2008-05-21
forum: Education &amp; Science
---

### Post by urgnom on 2008-05-21
Hi. I have some problems running the PSE gProms 3.1.2 application under Hardy. It installs, finds the license server and starts fine. When I try to run a simulation (or any other activity) I get the following message: 

Kernel process terminated unexpectedly with return code 127

And then nothing happens. Anyone got a solution? 
Would appreciate it...

---

### Post by urgnom on 2008-05-22
Solved (got answer from the guys making gProms). It requires the following libraries to be installed (but doesn't say in the documentation):

libgfortran1 libg2c0 refblas3 lapack3

If somebody should be interested. Have a great day!

---

