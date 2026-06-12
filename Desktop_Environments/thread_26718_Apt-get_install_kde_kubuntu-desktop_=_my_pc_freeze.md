---
title: "Apt-get install kde kubuntu-desktop = my pc freeze!"
date: 2005-04-13
forum: Desktop Environments
---

### Post by gnubios on 2005-04-13
Hi...

I have ubuntu 5.04, and i decide install kubuntu, but when i start konqueror or kcenter, the all system crash, all syatem!... mouse, keyboard, etc....

do you hear this problem before?

---

### Post by Molot on 2005-04-16
Hmm... I just started apt-get'ing kubuntu... If I'll get the same effect, I'll let you know how to solve it ;)

---

### Post by Molot on 2005-04-18
Standard Answer #1 - on my system works fine.

---

### Post by sharmaravi on 2005-04-20
Same problem here. Today I installed kubuntu-desktop through synaptic and it freezes  my system whenever I tried to open control center and konquerer. I did not try any other app. These were the first two I tried, got scared and came back to my sweet gnome. :)

*Update*
After reading somewhere in the forums, I disabled composite and removed 'RenderAccel' and 'AllowGLXWithComposite' in xorg.conf (I have nvidia card). Now, konquerer and control center do not freeze my system :D.

---

### Post by Molot on 2005-04-21
It is propably not package-specific error... At least, not on all systems it occures. I can run any programs (the two you pointed to too) without any problems.

Maybe send some more specific error info? Saying just "don't work" makes me to answer "works" ;-) but it can't help you, can it? Did you tried to look at logs or anything?

---

