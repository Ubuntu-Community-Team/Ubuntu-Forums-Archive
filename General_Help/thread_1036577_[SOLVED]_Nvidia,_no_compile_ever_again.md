---
title: "[SOLVED] Nvidia, no compile ever again?"
date: 2009-01-10
forum: General Help
---

### Post by Darkade on 2009-01-10
Hello! I have successfully installed official Nvidia modules successfully (look below if you are having problems with this), and been working fine with those for a while now. My only problem is that every time I upgrade the kernel I have to compile the modules again. Is there a way to prevent this to happen, without locking the kernel version in synaptic?



this is how I managed to install the modules
1. Downloaded the right modules from Nvidia site.
2. log out
3. CTRL-ALT-F1
4. log in
5. sudo killall gdm
6. sudo sh NVIDIA*.run

---

### Post by garnser on 2009-01-11
Since you're managing the nvidia drivers on your own you compile a custom version of the driver for each kernel you're using. When using synaptic an updated driver is attached with the kernel thus avoiding the problem.

So the simple answer is no, as long as you maintain the driver yourself you will have to recompile it when you change kernel.

---

### Post by 3rdalbum on 2009-01-11
If you use the Hardware Drivers manager, then your Nvidia drivers will remain in sync with your kernel. If you use Nvidia's own installer, it does not keep in sync with your kernel, and you need to compile again after every kernel upgrade. This is by design.

---

### Post by Darkade on 2009-01-11
:( Well guess I have to live with this or move to the open source module.
Thanks :D

---

### Post by ushimitsudoki on 2009-01-11
This is possible ... look at DKMS. No one is doing this for NVIDIA drivers, though, that I am aware of.

---

### Post by Darkade on 2009-01-11
> **ushimitsudoki said:**
> This is possible ... look at DKMS. No one is doing this for NVIDIA drivers, though, that I am aware of.
Thanks!! I've looked at that and I'm going to make some more reaserch about this [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") thanks again!!

---

### Post by Shazaam on 2009-01-11
There was a How-To posted on the forums to auto-reinstall the video drivers after a kernel update. You will have to search for it sorry.

---

