---
title: "Radeon Mobility 7500 drivers for ubuntu"
date: 2006-07-29
forum: Desktop Environments
---

### Post by LORD_PoLvO on 2006-07-29
hey all i need some help really bad!, my friend has finaly decided (after a little persuasion) to use linux and being an ubuntu user i offered to set up his laptop for him, i have everything running fine, but i need help in the video adapter appartment. i have never use ATI graphics cards before and soon AFTER installing ubuntu i found out that he was using a Radeon Mobility 7500 graphics adapter, i would like some help in setting up this card so that it is acellerated so my friend can play his games etc, please if anyone can help   that would be great :)


peace out, polvo

---

### Post by LORD_PoLvO on 2006-07-29
*bump*

---

### Post by LORD_PoLvO on 2006-07-29
*bump*

---

### Post by LORD_PoLvO on 2006-07-31
hey, i posted a thread asking help about this a day ago and was complely ignored lol, hence the name so ill ask again.


i am having trouble setting up ati drivers on my friends laptop and its bothering me because he wants to use linux but will only do so if he can have his ati gfx working.

i have made a little progress but still am getting nowhere here is the install log atm

```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2230: warning: ‘deferred_flush’ defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.
```




PLEASE SOME ONE HELP ME, ty in advance.

---

### Post by x64Jimbo on 2006-07-31
It would be a lot simpler if you installed from the repositories instead of trying to configure it yourself. Open your package manager and search for ati

---

### Post by matthew on 2006-07-31
> **LORD_PoLvO said:**
> hey, i posted a thread asking help about this a day ago and was complely ignored lol, hence the name so ill ask again.

If your question hasn't been answered it's either because no one knows the answer, because you weren't specific enough in the details given with your question, or because you just need to be a bit more patient.

I'm merging this back into your original thread. Please don't post the same question more than once. I would also like to suggest reading the following links in my signature; "how to help yourself" and "unanswered thread."

---

### Post by Ares Drake on 2006-07-31
btw: ati claims on their site, the fglrx drivers are only for radeon >= 8500
but maybe the "radeon" driver will work?

---

### Post by x64Jimbo on 2006-07-31
Can't hurt to give it a shot. The fglrx driver worked for my Radeon XPress 200, but do whatever suits you best.

---

### Post by LORD_PoLvO on 2006-07-31
> **Ares Drake said:**
> btw: ati claims on their site, the fglrx drivers are only for radeon >= 8500
but maybe the "radeon" driver will work?

where can i get the "radeon" driver just from [www.ati.com](www.ati.com) ?? sorry for this noobie question but this is seriously the first time i have even used A computer with an ati graphics card.

---

### Post by x64Jimbo on 2006-07-31
Fire up your package manager and search for ATI. it'll be in there.

---

### Post by Ares Drake on 2006-07-31
If I remember correctly, you need to install something vaguely like xorg-driver-radeon (i.e. with Synaptic), and make a change to the xorg.conf to use the driver "radeon". Happy hunting!

---

### Post by jasutton on 2006-07-31
IIRC, the 'ati' driver (the open source ATI driver that provides limited 3D capibilities to older ATI cards) defers to the 'radeon' driver when necessary  (so you could use either 'ati' or 'radeon' in the driver portion of your xorg.conf with the same result).  By the way, the package you're looking for is 'xserver-xorg-driver-ati' but I think it's installed by default in K/Ubuntu...

---

