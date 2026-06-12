---
title: "Kernel Problems"
date: 2005-12-22
forum: Desktop Environments
---

### Post by Blind on 2005-12-22
When I boot ubuntu after the "Dell" screen I get a menu, it is up for 2 seconds. If I press escape it brings me to a menu. If I boot the 12-10-386 kernel it wont run, and if it does the X server doesn't load. If I boot the 12-9-386 kernel it boots fine. Is there a way to fix the 12-10-386 kernel or make the 12-9-386 default?

---

### Post by antidrugue on 2005-12-22
What's your machine?

Post the output of
```

cat /proc/cpuinfo

```

You could just uninstall linux-image-2.12.10-2-386.

Or maybe you need some modules to get it running?

What's the output of
```

dpkg -l | grep 386

```

---

### Post by Blind on 2005-12-22
Results of cat /proc/cpuinfo:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.00GHz
stepping        : 4
cpu MHz         : 1994.452
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3948.54

```

Results of dpkg -l | grep 386:
```
ii  linux-386                                            2.6.12.16.1             Complete Linux kernel on 386.
ii  linux-image-2.6.12-10-386                            2.6.12-10.24             Linux kernel image for version 2.6.12 on 386
ii  linux-image-2.6.12-9-386                             2.6.12-9.23             Linux kernel image for version 2.6.12 on 386
ii  linux-image-386                                      2.6.12.16.1             Linux kernel image on 386.
ii  linux-restricted-modules-2.6.12-10-386               2.6.12.4-11.1             Non-free Linux 2.6.12 modules on 386
ii  linux-restricted-modules-2.6.12-10-386-nvidia-legacy 2.6.12.4-11.1             Non-free Linux 2.6.12 NVIDIA legacy module o
ii  linux-restricted-modules-2.6.12-9-386                2.6.12.4-11             Non-free Linux 2.6.12 modules on 386
ii  linux-restricted-modules-386                         2.6.12.16.1             Restricted Linux modules on 386.
```

---

### Post by antidrugue on 2005-12-22
[FONT=Arial][SIZE=2][COLOR=Sienna]It seems that the only difference between your installation of
2.6.10-2-386 and 2.6.9-2-386 is this:

linux-restricted-modules-2.6.12-10-386-nvidia-legacy

which you could uninstall

```

sudo apt-get remove --purge linux-restricted-modules-2.6.12-10-386-nvidia-legacy

``` 

Well, anyway. If 2.6.9-2-386 works for you, then I suggestion you just
install its 686 equivalent.

```

sudo apt-get install linux-image-2.6.9-2-686 linux-restricted-modules-2.6.9-2-686

``` 
Regarding you first question,
> 
Is there a way to fix the 12-10-386 kernel or make the 12-9-386 default?
 
you just have to edit the file /boot/grub/menu.lst.

You will see at the top a line like that:
```

default         0

``` 
Which means item number 1 is default. For the item number three to be default, you must have
```

default         2

``` 
Hope this help.

[/COLOR]        
[/SIZE][/FONT]

---

### Post by Blind on 2005-12-22
This worked perfect, thanks.

---

### Post by antidrugue on 2005-12-22
You're welcome.

Have fun!

---

