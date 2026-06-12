---
title: "Which command executes the system bell?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by kapetanski on 2005-08-09
Hi, I installed lm-sensors yesterday and as I am planning to put my comuter in a sound damped box I therefore want to create an alarm if the temperature reaches a critical level. So, I am running kubuntu, and I hope it is possible to make a script which executes the system bell, and then choose this file in the control center, in the options regarding kde system guard. I am new to linux and maybe there is another way to do this, I really would appreciate tips.

---

### Post by az on 2005-08-09
printf "\a" (maybe echo from the command line)

or:
[http://packages.ubuntu.com/hoary/sound/beep](http://packages.ubuntu.com/hoary/sound/beep)

or:
[http://packages.ubuntu.com/hoary/sound/softbeep](http://packages.ubuntu.com/hoary/sound/softbeep)

---

