---
title: "Possible to add a driver to lm-sensors? (adt7475)"
date: 2009-01-22
forum: General Help
---

### Post by ctarwater on 2009-01-22
Here's the deal,

lm-sensors finally has a driver for the adt7475 chip found on many ASUS motherboards, allowing us to control fan speed via pwmcontrol.

Unfortunately I can't have it until kernel 2.6.29...

Is there any way around that short of compiling the 2.6.29RC or Jaunty?

---

### Post by dcstar on 2009-01-22
> **ctarwater said:**
> Here's the deal,

lm-sensors finally has a driver for the adt7475 chip found on many ASUS motherboards, allowing us to control fan speed via pwmcontrol.

Unfortunately I can't have it until kernel 2.6.29...

Is there any way around that short of compiling the 2.6.29RC or Jaunty?

You can compile any kernel you like for your system, there are various HOWTOs around with detailed instructions.

---

### Post by ctarwater on 2009-01-22
I understand that I can compile any kernel, but I am curious if that is in fact the only option available in this case.  Or at least the only option that results in me being able to use that driver.

---

### Post by dcstar on 2009-01-22
> **ctarwater said:**
> I understand that I can compile any kernel, but I am curious if that is in fact the only option available in this case.  Or at least the only option that results in me being able to use that driver.

You need the hardware support in the kernel, otherwise no application can use the hardware.

---

### Post by ctarwater on 2009-01-22
Ah, makes sense.

Thanks.

Time to start reading about compiling the kernel...

---

### Post by dcstar on 2009-01-30
> **ctarwater said:**
> Ah, makes sense.

Thanks.

Time to start reading about compiling the kernel...

I found that you can get kernels for newer versions to use at:

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

I use the following repository string for my 8.04 system:

```
deb http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main
```

One warning, I couldn't find a Nvidia driver (or get one to install) with the newer kernels. Possibly it could be done, but I could not manage it.

---

