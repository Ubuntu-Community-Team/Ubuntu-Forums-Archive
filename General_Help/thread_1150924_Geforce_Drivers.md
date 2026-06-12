---
title: "Geforce Drivers?"
date: 2009-05-06
forum: General Help
---

### Post by DrMilo on 2009-05-06
LO all! 

I just purchased a e-geforce 7200 gs graphics card and I want to add the Nvidia drivers from synaptic. However, there seems to be lots of drivers there and I'm wondering if I should add them all and let God sort them out or whether I need specific drivers. Thanks in advance!

---

### Post by rajeev1204 on 2009-05-06
Install nvidia-glx-180 for jaunty jackalope 9.04

---

### Post by RedSingularity on 2009-05-06
Did you look in hardware drivers?  Usually they are in there.

---

### Post by LowSky on 2009-05-06
got to system > admin > drivers

pick the newest one..

good luck

---

### Post by DrMilo on 2009-05-06
> **LowSky said:**
> got to system > admin > drivers

pick the newest one..

good luck

Thanks! I settled on NVIDIA binary XFree86 4.x/X.Org 'new' driver. I seem to have improved matters on my old video card!

Now I've also got this 

NVIDIA-Linux-x86-180.51-pkg1.run 

on my desktop and it won't install; screenshot attached. I also get "command not found" in terminal. Anyone know if I can get that installed, without compiling I hope!

Thanks again for the help!

---

### Post by DrMilo on 2009-05-06
> **rajeev1204 said:**
> Install nvidia-glx-180 for jaunty jackalope 9.04

I don't think that I know how to do that, I'm using Hardy, sorry, should have mentioned that at the start.

---

### Post by RedSingularity on 2009-05-06
Same thing......sudo apt-get install nvidia-glx-180
in terminal.

---

### Post by DrMilo on 2009-05-06
> **Shadow121 said:**
> Same thing......sudo apt-get install nvidia-glx-180
in terminal.

K thanks!

---

### Post by DrMilo on 2009-05-06
> **Shadow121 said:**
> Same thing......sudo apt-get install nvidia-glx-180
in terminal.

Actually it looks like it won't work that way in Hardy:

E: Couldn't find package nvidia-glx-180

Not sure that I want to upgrade the whole OS over a driver.

---

### Post by RedSingularity on 2009-05-06
I see it in synaptic......try going into synaptic and searching for it with the "search" option.  Maybe the name is a little different..

---

### Post by DrMilo on 2009-05-07
> **Shadow121 said:**
> I see it in synaptic......try going into synaptic and searching for it with the "search" option.  Maybe the name is a little different..

I can't find it. Perhaps I need to enable something?

---

### Post by RedSingularity on 2009-05-07
Do you have Universe and Multiverse enabled?

---

### Post by rajeev1204 on 2009-05-08
> **DrMilo said:**
> I can't find it. Perhaps I need to enable something?

You have the correct drivers nvidia-glx-new.

Its version 173 or 177 in hardy.

After restart did you get to a graphical desktop?

GO to system>administration>restricted drivers( or hardware drivers whichever name) and enable nvidia.

---

### Post by DrMilo on 2009-05-08
> **rajeev1204 said:**
> You have the correct drivers nvidia-glx-new.

Its version 173 or 177 in hardy.

After restart did you get to a graphical desktop?

I've got that installed, and it's an improvement, but it seems that the 180.x drivers are notably better, and I was hoping to try them out.

> GO to system>administration>restricted drivers( or hardware drivers whichever name) and enable nvidia.


I think that's only in Ibex and up, I don't have either menu option.

---

### Post by DrMilo on 2009-05-08
> **Shadow121 said:**
> Do you have Universe and Multiverse enabled?


Yup.

---

### Post by rajeev1204 on 2009-05-10
> **DrMilo said:**
> I've got that installed, and it's an improvement, but it seems that the 180.x drivers are notably better, and I was hoping to try them out.



I think that's only in Ibex and up, I don't have either menu option.

You need to upgrade to jaunty for that,or try to compile the drivers from nvidia site( not recommended)

On the second point,This feature has been since feisty fawn 7.04 and is present in hardy too.

---

