---
title: "HZ 1000 kernel for intrepid"
date: 2009-02-12
forum: General Help
---

### Post by abracadaver on 2009-02-12
Is there an official ubuntu kernel for intrepid that has HZ = 1000 that I can just apt-get?  There used to be a low-latency for fiesty maybe, but I can't find it for intrepid.

Thanks!
-Shawn

---

### Post by dcstar on 2009-02-12
> **abracadaver said:**
> Is there an official ubuntu kernel for intrepid that has HZ = 1000 that I can just apt-get?  There used to be a low-latency for fiesty maybe, but I can't find it for intrepid.

Thanks!
-Shawn

I think all the "generic" kernel use 1000Hz, the server ones are 100Hz and I don't know that the RT ones are.

---

### Post by abracadaver on 2009-02-12
> **dcstar said:**
> I think all the "generic" kernel use 1000Hz, the server ones are 100Hz and I don't know that the RT ones are.

OK, I dont' know what you mean.  I used the mini.iso and installed (Linux xxx 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux).  When I "grep -r HZ /usr/include/" the only thing that looks like a define for HZ is:

/usr/include/asm/param.h:#define HZ 100

Thanks!
-Shawn

---

### Post by abracadaver on 2009-02-12
As a side note, is there any way I can determine this without greping source files?  Can I use a function or something else to determine the constants in the running kernel?  echo something?

Thanks!
-Shawn

---

### Post by dcstar on 2009-02-12
> **abracadaver said:**
> As a side note, is there any way I can determine this without greping source files?  Can I use a function or something else to determine the constants in the running kernel?  echo something?

Thanks!
-Shawn

It is not in the source, it is set in the kernel .config file which is used in the compilation process.

---

### Post by abracadaver on 2009-02-13
Great, so how to determine on my system?

Thanks!
-Shawn

---

### Post by abracadaver on 2009-02-13
After some searching I looked here:

$ grep HZ /boot/config-2.6.24-23-generic
# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=250
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
CONFIG_MACHZ_WDT=m
CONFIG_NO_HZ=y

Is this correct, it is at 250?

Any help here?

Thanks!
-Shawn

---

### Post by dcstar on 2009-02-13
> **abracadaver said:**
> After some searching I looked here:

$ grep HZ /boot/config-2.6.24-23-generic
# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=250
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
CONFIG_MACHZ_WDT=m
CONFIG_NO_HZ=y

Is this correct, it is at 250?

Any help here?

Thanks!
-Shawn

That seems to be right, you can just change that and recompile the kernel (search out the many kernel compilation HOWTOs for detailed instructions).

---

### Post by abracadaver on 2009-02-13
Well generic kernels seem to be 250 HZ.  I Installed linux-kernel-rt and it seems to be at 1000.

-Shawn

---

### Post by sdennie on 2009-02-13
The -generic kernel is 250Hz and I believe the server kernel is 100Hz but, the -rt kernel is compiled for 1000Hz.  I believe it also has patches to make the kernel more suitable for low latency tasks (which is why I'm assuming you want to change to 1000Hz).  You should be able to install it with:

```

sudo apt-get install linux-rt

```

---

### Post by abracadaver on 2009-02-13
Yes, thanks I did that, hence my post that I installed linux-image-rt.  :-)

---

### Post by sdennie on 2009-02-13
If you look at the timestamps, you posted as I was writing my response.  ;)

---

### Post by alex_o on 2010-05-05
> **sdennie said:**
> **The -generic kernel is 250Hz** and I believe the server kernel is 100Hz but, the -rt kernel is compiled for 1000Hz.  I believe it also has patches to make the kernel more suitable for low latency tasks (which is why I'm assuming you want to change to 1000Hz).  You should be able to install it with:

```

sudo apt-get install linux-rt

```

that isnt true in ubuntu 10.04(2.6.32-20-generic)

```
grep HZ /boot/config-`uname -r`
```

```
CONFIG_NO_HZ=y
CONFIG_HZ_100=y
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
**CONFIG_HZ=100**
CONFIG_MACHZ_WDT=m
```

can i simply replace **CONFIG_HZ=100** with **CONFIG_HZ=1000** without recompiling?

if you are about to say just install the rt kernel, i dont want to because the rt kernel's are always 10 or 20 kernels old :(

---

### Post by dcstar on 2010-05-05
> **alex_o said:**
> 
........
can i simply replace **CONFIG_HZ=100** with **CONFIG_HZ=1000** without recompiling?


It is a compiler directive. It sets things during the compilation process.

---

