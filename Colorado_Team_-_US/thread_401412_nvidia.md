---
title: "nvidia"
date: 2007-04-04
forum: Colorado Team - US
---

### Post by amonroe on 2007-04-04
I installed ubuntu 7.04 on restart my video card needed configing sudo envy useto work but i got this message your graphic card is supported by nvidia drivers your operative system does not seem to be supported by envy. what should i do

---

### Post by joey on 2007-04-05
The simple answer to not to use ENVY but use the restricted driver manager that ships with Feisty instead.

---

### Post by davidvasta on 2007-04-16
The way ENVY works is not supported in Feisty. He is working on the next version of Envy to support Feisty. The graphics engine changed and he has to rewrite some stuff. I am in the same boat. I use ENVY now with 6.10 and have an nVidia card. I tried Feisty on here and it was not to my liking. I hope they iron out the kinks and make it better with nVidia.

---

### Post by Caseyjp on 2007-04-21
I'm still not completely sure why folks 'have' to use envy.  With dependencies met, the NVIDIA installer works just fine here.  The ONLY thing I had to do upon the fiesty upgrade was to run it against the new kernel,and then edit: 

/etc/default$ nano linux-restricted-modules-common


and change this line from this:   DISABLED_MODULES=""  

to this:

DISABLED_MODULES="nv".

As long as that line is there disabling the default nvidia restricted module, then using the nvidia installer works just fine.  This has allowed me for the last year to update or downgrade the nvidia driver at will.  

The ONLY thing is that you MUST run the installer anytime you install a new kernel.

As a Colorado Ubuntu/linux user I say 'hello'.  

I'm also a hardcore Eve Online player, and test it with wine over at winehq, as well as a cedega emerald status user.

This is NOT a knock on ENVY or Alberto Milone's project.  If the user belongs firmly in the top forum section, then sure.  Once you get used to how linux works, how things install, and have a better grasp of "how to" then using the binary installer works fine.

---

