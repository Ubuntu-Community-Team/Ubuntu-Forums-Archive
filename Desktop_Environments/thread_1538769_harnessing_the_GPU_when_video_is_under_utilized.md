---
title: "harnessing the GPU when video is under utilized"
date: 2010-07-25
forum: Desktop Environments
---

### Post by jflaker on 2010-07-25
Is there any way to harness the under-utilized GPU to increase processing power of my PC?

There is much potential in the GPU for stuff like BOINC (Seti, etc).  HOW do I harness the under-utilized processing power in my nVidia card?

Thanks

---

### Post by jflaker on 2010-07-26
No one????

---

### Post by Mr_Speedy on 2010-07-27
[http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu](http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu)

Here is how to install BOINC on Ubuntu, however I have no idea if it will utilize the graphics card...  however there is one way to find out..... try it  :)

---

### Post by jflaker on 2010-07-27
I already have it installed and have been running it for almost 3 years now.  I was hoping someone knew if there was a way to get the GPU involved in not only BOINC, but other things that I am doing on my system.

---

### Post by cascade9 on 2010-07-27
CUDA will, but its limited in what it can be used for, 

> Current and Future usages of CUDA Architecture 
[LIST]
[*]Accelerated rendering of 3D graphics
[*][Real Time Cloth Simulation OptiTex.com]("http://www.optitex.com/images/downloads/Nvidia_CUDA_SS_OptiTex_FINAL.pdf") - Real Time Cloth Simulation
[*]Distributed Calculations, such as predicting the native conformation of [proteins]("http://en.wikipedia.org/wiki/Proteins")
[*]Medical analysis simulations, for example [virtual reality]("http://en.wikipedia.org/wiki/Virtual_reality") based on [CT]("http://en.wikipedia.org/wiki/X-ray_computed_tomography") and [MRI]("http://en.wikipedia.org/wiki/Magnetic_resonance_imaging") scan images.
[*]Physical simulations, in particular in [fluid dynamics]("http://en.wikipedia.org/wiki/Fluid_dynamics").
[*]Environment statistics
[*]Accelerated [encryption]("http://en.wikipedia.org/wiki/Encryption"), [decryption]("http://en.wikipedia.org/wiki/Decryption") and [compression]("http://en.wikipedia.org/wiki/Data_compression")
[*]Accelerated interconversion of video file formats
[*]Artificial intelligence
[/LIST]


[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

---

### Post by 3rdalbum on 2010-07-27
> **jflaker said:**
> I already have it installed and have been running it for almost 3 years now.  I was hoping someone knew if there was a way to get the GPU involved in not only BOINC, but other things that I am doing on my system.

GPUs talk a completely different language to CPUs. Programs need to be specially rewritten in order to offload their processing to the GPU. Some sorts of programs wouldn't even benefit from GPU processing anyhow.

So, in other words, the answer to your question is no. Not yet, at least.

---

### Post by jflaker on 2010-07-27
Sad.  There is so much processing power which generally just goes to waste.  I believe that Windows7 has the ability, but not sure if it is an addon or by design.....or so I hear.

---

