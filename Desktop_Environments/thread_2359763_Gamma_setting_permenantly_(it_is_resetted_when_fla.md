---
title: "Gamma setting permenantly (it is resetted when flash is activated)"
date: 2017-04-27
forum: Desktop Environments
---

### Post by breathejustice on 2017-04-27
I am using ubuntu 16.04 unity desktop.

I made the following script with the file name gammasetting.sh, and make it executable.

[FONT=courier new]#!/bin/bash
sleep 20
xgamma -ggamma 0.69
xgamma -bgamma 0.71
xgamma -rgamma 0.73
[/FONT]

Then added it to "startup application"

It works at the first booting, 
But when I use adobe flash player, the gamma is resetted to 1.0

I want to fix and continue the gamma value with the above setting of gammasetting.sh file even when I use flash player
How should I solve it?

---

