---
title: "Dapper kernel SMP support??"
date: 2006-06-17
forum: Desktop Environments
---

### Post by timm on 2006-06-17
Hello all,

First of all, I am very impressed with the smoothness of the installation process. Going from a live environment to do a quick hardware support check to installing the OS was brilliant. 

I've got an Intel Pentium D / 945 - based machine. I had originally installed FC5, but like Ubuntu much better. The issue is that FC5 seemed to have SMP support in the kernel or could detect to use an SMP kernel. Ubuntu appears not to see the 2nd core. I guess I'll just have to build a custom kernel, but is there an easier workaround for this issue? 

Thanks,
Tim

---

### Post by astoltz on 2006-06-17
Search in synaptic for 'smp'.  I think the kernel you want is kernel-image-2.4.27-2-686-smp

---

### Post by Dubbayoo on 2006-06-17
[QUOTE=astoltz]Search in synaptic for 'smp'.  I think the kernel you want is kernel-image-2.4.27-2-686-smp[/QUOTE]

why 2.4.x instead of 2.6.15.x?

---

### Post by angkor on 2006-06-17
smp is built-in in the kernel in dapper:

```
apt-cache search linux-image
linux-image-2.6.15-23-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-23-686 - Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV **SMP**/UP
linux-image-2.6.15-23-k7 - Linux kernel image for version 2.6.15 on AMD K7 **SMP**/UP
linux-image-2.6.15-23-server - Linux kernel image for version 2.6.15 on Server Equipment
linux-image-2.6.15-23-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-image-2.6.15-25-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-25-686 - Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV **SMP**/UP
linux-image-2.6.15-25-k7 - Linux kernel image for version 2.6.15 on AMD K7 **SMP**/UP
linux-image-2.6.15-25-server - Linux kernel image for version 2.6.15 on Server Equipment
linux-image-2.6.15-25-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-image-386 - Linux kernel image on 386.
linux-image-686 - Linux kernel image on PPro/Celeron/PII/PIII/PIV.
linux-image-k7 - Linux kernel image on AMD K7.
linux-image-server - Linux kernel image on Server Equipment.
linux-image-server-bigiron - Linux kernel image on BigIron Server Equipment.
```

So if you want to use the second core in your pentium:

```
sudo apt-get install linux-image-686
```

and a reboot will do the trick.

Don't install the 2.4 kernel.

---

### Post by astoltz on 2006-06-17
Yeah, sorry about the 2.4 thing.  I must have pasted the wrong line fron my search.  2.6.... is what you want.

---

### Post by helpdeskdan on 2006-06-17
Out of curiosity; has anybody noticed a performance difference by using a different kernel?  I have a dual pentium2 and I'm wondering if it's worth my time to bother downloading the 686 image.  (And recompile Mplayer.  My goal in life: optimized Mplayer)

---

