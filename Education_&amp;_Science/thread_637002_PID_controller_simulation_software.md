---
title: "PID controller simulation software?"
date: 2007-12-10
forum: Education &amp; Science
---

### Post by Joakim Stokland on 2007-12-10
Hi!
Does anyone know if there exists some kind of software for Linux to simulate a process controlled by a PID controller? Perhaps where you could choose between a few different processes, adjust the PID parameters and maybe even simulate a cascade control loop?
I want this software to practice tuning controllers. I once had some Swedish software that did all this (it's name is Regulär), but it was a Windows app, and I don't have it anymore.

Thanks!
Joakim

---

### Post by rajpal on 2008-09-16
.........................

---

### Post by Proton Soup on 2008-09-19
looks like Scilab/Scicos has a function block for this.  and i wouldn't be surprised if Octave also has at least the tools to roll your own.

edit: i guess this link is better than cut'n'pasting the help

[http://www.scilab.org/product/man/index.php?module=scicos&page=PID.htm](http://www.scilab.org/product/man/index.php?module=scicos&page=PID.htm)

---

### Post by glinsvad on 2008-10-07
LabView does a neat job with tons of PID examples, but it is of course not free. Otherwise, I'm quite sure there are many C/C++ implementation of PID control, e.g.:
[http://www.linuxpcrobot.org/?q=node/4]("http://www.linuxpcrobot.org/?q=node/4")

---

### Post by crispus on 2008-10-07
Hi Joakim,

Scilab/Scicos will give you a block diagram environment for this kind of simulation and would be the closest (free) thing to Simulink.

Octave has some very good Control System functions which will be familiar to Matlab users but may not be so visual.

In either case you can work with Transfer Function or State Space plant models (presuming you have them).

I don't know of any 'ready made' packages which are solely designed for control system simulation & tuning but if you have a bit of background knowlege of systems & control theory then these options should do the job nicely.

Crispus

---

