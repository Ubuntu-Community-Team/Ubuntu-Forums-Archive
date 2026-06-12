---
title: "nVidia CUDA and PyCUDA for 11.04?"
date: 2011-08-17
forum: Education &amp; Science
---

### Post by Patrickdlg on 2011-08-17
I am currently working on speeding some code up for a spiking neural network simulation and want to make use of my GPU (nVidia GeForce GTX 560M).  I have seen several tutorials and guides for installing CUDA on 10.10 but nothing concerning 11.04.  If anybody has any experience with this, your help is appreciated.  Thanks.

---

### Post by aeftimia on 2011-08-18
There is a ppa for all cuda stuff here:
[https://launchpad.net/~aaron-haviland/+archive/cuda-4.0](https://launchpad.net/~aaron-haviland/+archive/cuda-4.0)
and the latest nvidia is found here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Sorry, I have not heard of pycuda. Maybe someone has a ppa for that too?

---

### Post by Patrickdlg on 2011-08-25
Thanks for those links, aeftimia.  I will use those for setting up X.  I was afraid to update my headers because I manually installed the latest nVidia driver.  I have CUDA up and running, but pyCUDA is giving me some trouble.  When I execute a program, I keep getting an error saying that 'nvcc' was not on the path; I have seen similar problems posted online, but I am unsure of how to fix it.

---

### Post by Sc0urgeTR on 2011-09-15
[http://wiki.tiker.net/PyCuda/Installation/Linux/Ubuntu](http://wiki.tiker.net/PyCuda/Installation/Linux/Ubuntu)

I don't know a lot about pyCUDA from what I can tell it's a IDE for coding CUDA cores. 
But that might help with the installation of the program. :3 good luck

---

