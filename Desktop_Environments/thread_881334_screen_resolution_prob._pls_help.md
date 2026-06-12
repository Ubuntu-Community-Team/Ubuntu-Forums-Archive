---
title: "screen resolution prob. pls help"
date: 2008-08-05
forum: Desktop Environments
---

### Post by jlo-linux on 2008-08-05
i activate my desktop effects, then my screen resolution adjust to 800x600, and im sick of 800x600 i want it to back at 1024x768..


what is the problem??? my graphics card is an old model of geForce MX.. hmm my 2nd day using ubuntu

---

### Post by pietjanjaap on 2008-08-06
Without desktop effects did you have all the possible screen sizes that should be possible with your videocard?
This means does ubuntu know wich videocard you have?

Try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by jlo-linux on 2008-08-06
yup. the first one i've install nvidia driver is for the newer models. then i removed that and change to old drivers for nvidia.. 

but my login  resolution is 1024x768.. when desktop start it goes to 800x600..

oryt im going to try what u said.. tnx

---

