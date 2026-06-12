---
title: "add/remove"
date: 2006-06-13
forum: Desktop Environments
---

### Post by ozarkman on 2006-06-13
when I first installed ubuntu I used automatix to install a few things. I have since removed it and now when i try to launch add/remove (I did not try this befor the automatix install btw) it fails to start.

Is my install corrupt or did automatix break something? I could just reinstall the whole os but would rather figure out what I did wrong instead.

---

### Post by zxee on 2006-06-13
What output do you get if you type sudo synaptic <enter> in a terminal?
You can also try it without the sudo-you normally would just get a message that you're not running 
the package manager as root. I have automatix installed on 6.06 and synaptic still works fine. 
How did you remove automatix?

---

### Post by ozarkman on 2006-06-13
tried in the terminal and said i had to be in root so i changed to the root terminal. at root the synaptic package manager started.

sorry i know enough to be dangerious im shure this is clear to all by now :-P

---

### Post by zxee on 2006-06-13
[QUOTE=ozarkman]tried in the terminal and said i had to be in root so i changed to the root terminal. at root the synaptic package manager started.

sorry i know enough to be dangerious im shure this is clear to all by now :-P[/QUOTE]

:) We're all learning all the time. Synaptic should open from the menu also-so something is not right.

---

### Post by ozarkman on 2006-06-13
[QUOTE=zxee]
How did you remove automatix?[/QUOTE]

sudo apt-get remove automatix

---

