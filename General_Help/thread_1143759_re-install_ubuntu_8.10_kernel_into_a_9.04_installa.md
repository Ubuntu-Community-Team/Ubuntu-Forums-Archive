---
title: "re-install ubuntu 8.10 kernel into a 9.04 installation?"
date: 2009-04-30
forum: General Help
---

### Post by jofre on 2009-04-30
i everyone, 

I have finished installing xubuntu 9.04. It looks great, but... I am experiencing a huge degradation in performance. I should be more explicit, I do not mean, desktop tasks. I run molecular dynamics simulations in my laptop, and the same code, it runs at least 50 times slower.

The suspect is the kernel (current kernel: 2.6.28-11-generic). So I was wondering if it there is a way to re-install the kernel from ubuntu 8.10 without re-installing ubuntu.

Thanks in advance,
Jofre

---

### Post by jofre on 2009-05-07
Hi everyone, 

I did found a blog where it was explained:

[http://thanhsiang.org/faqing/node/129](http://thanhsiang.org/faqing/node/129)


I also installed KernelCheck, so I downloaded also the latest kernel 2.29.x and compiled, and the my laptop still is much, much slower!!! As I said earlier, I do not feel a difference for everyday taks, but when I run any program in fortran or in octave, the decrease in performance is truly worring. 

I would appreciate if somebody could give me a hint. What could I disabled? It is the new xfce4.6.0? Maybe I just should go back to 8.10?

---

### Post by skymera on 2009-05-07
Here's a list of kernels for Ubuntu:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Hmm slowdowns. What is your graphics card? Does it happen to be an Intel chip?

---

### Post by jofre on 2009-05-07
The graphic card is an nvidia, but nevertheless, the fortran and octave programs do not used the graphic card.

Thanks for the link,
Jofre

---

### Post by chitek on 2009-05-21
Will this cause it to give you the option when you boot to choose a kernel?

---

